# CIS Compliance

These images are **systemd-enabled Ansible test targets** (primarily for Molecule).
That purpose requires a handful of deliberate deviations from CIS hardening
guidance. Everything else is scanned continuously and kept clean.

## Scanning

The [CIS compliance scan workflow](.github/workflows/cis-scan.yml) runs on every
Dockerfile change and weekly (Mondays), covering all images:

| Tool | Covers | Output |
|---|---|---|
| Trivy | OS package vulnerabilities (HIGH/CRITICAL) | SARIF → GitHub code scanning (`trivy-<distro>`) |
| Trivy compliance | CIS Docker Community Edition Benchmark (image controls) | Job log report |
| Dockle | Image configuration lint (CIS Docker best practices) | SARIF → GitHub code scanning (`dockle-<distro>`) |
| Hadolint | Dockerfile build best practices (CIS Docker §4) | SARIF → GitHub code scanning (`hadolint-<distro>`) |

New code-scanning alerts are forwarded to the maintainer webhook by
[`code-scanning-notify.yml`](.github/workflows/code-scanning-notify.yml).

Image integrity is separately guaranteed by cosign keyless signatures — see
"Verifying Image Signatures" in the [README](README.md).

## Accepted deviations

These findings are intentional and will not be "fixed" — they are what makes the
images usable as Ansible/Molecule test targets that emulate real hosts:

| Deviation | CIS / scanner reference | Why it is required |
|---|---|---|
| Container runs as `root` with systemd as PID 1 | CIS Docker 4.1, Dockle CIS-DI-0001 | Test targets must boot systemd to exercise service/handler tasks like a real host |
| Designed to run with `--privileged` and a cgroup mount | CIS Docker 5.4/5.5 | systemd inside a container needs privileged mode and `/sys/fs/cgroup` |
| `sudo` installed, `requiretty` disabled | CIS distro benchmarks (sudo hardening) | Ansible `become` over non-tty connections must work |
| Python build toolchain and pip present in final image | Image-minimalism guidance | Ansible and its dependencies are the product; roles under test may compile wheels |
| No `HEALTHCHECK` | CIS Docker 4.6, Dockle CIS-DI-0006 | Containers are short-lived test targets managed by Molecule, not services |
| OS/pip packages deliberately unpinned | Hadolint DL3008/DL3013/DL3041 (ignored via `.hadolint.yaml`) | Every rebuild must pull the newest packages so published CVE fixes land automatically |
| Trivy secret scanner disabled in the vuln scan | `scanners: vuln` in cis-scan.yml | The Ansible pip package ships dummy SSH keys and example AWS/JWT credentials as test fixtures, producing 100+ false-positive "leaked secret" alerts |
| CVEs without a published distro fix not reported | `ignore-unfixed: true` in cis-scan.yml | Nothing to act on until the distro publishes a fix; full unfiltered list stays visible in the compliance report job log |

Any deviation not listed here that a scan reports is a genuine finding and
should be fixed or added to this table with justification via pull request.

## Scope notes

- The CIS **Docker Benchmark** host/daemon sections (1.x–3.x) apply to the
  machine running the containers, not to these images.
- The CIS **distribution benchmarks** (e.g. CIS Debian 12, CIS AlmaLinux 9)
  target full OS installs; most controls (partitioning, kernel modules,
  auditd, firewall) are not applicable inside a container image and are not
  claimed here.
