# Docker Ansible Images

[![CIS scan](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/cis-scan.yml?label=CIS%20scan&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/cis-scan.yml)
[![Signed with cosign](https://img.shields.io/badge/images-signed%20with%20cosign-2f80ed?logo=sigstore)](#verifying-image-signatures)
[![CIS compliance](https://img.shields.io/badge/CIS-compliance%20notes-blue)](COMPLIANCE.md)
[![Renovate](https://img.shields.io/badge/renovate-enabled-brightgreen?logo=renovate)](renovate.json)
[![License](https://img.shields.io/github/license/iamenr0s/docker-ansible-images)](LICENSE)

This repository contains a Dockerfile and necessary files to build a Docker image based on different operative systems that enables systemd service management, mounts the cgroup volume, and installs an Ansible inventory file.

## Available Images

| Build | Quay.io | Docker Hub |
|---|---|---|
| [![almalinux8](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/almalinux8.yml?label=almalinux8&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/almalinux8.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-almalinux8.json)](https://quay.io/repository/iamenr0s/docker-almalinux8-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-almalinux8-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-almalinux8-ansible) |
| [![almalinux9](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/almalinux9.yml?label=almalinux9&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/almalinux9.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-almalinux9.json)](https://quay.io/repository/iamenr0s/docker-almalinux9-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-almalinux9-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-almalinux9-ansible) |
| [![almalinux10](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/almalinux10.yml?label=almalinux10&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/almalinux10.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-almalinux10.json)](https://quay.io/repository/iamenr0s/docker-almalinux10-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-almalinux10-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-almalinux10-ansible) |
| [![debian10](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/debian10.yml?label=debian10&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/debian10.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-debian10.json)](https://quay.io/repository/iamenr0s/docker-debian10-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-debian10-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-debian10-ansible) |
| [![debian11](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/debian11.yml?label=debian11&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/debian11.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-debian11.json)](https://quay.io/repository/iamenr0s/docker-debian11-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-debian11-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-debian11-ansible) |
| [![debian12](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/debian12.yml?label=debian12&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/debian12.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-debian12.json)](https://quay.io/repository/iamenr0s/docker-debian12-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-debian12-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-debian12-ansible) |
| [![debian13](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/debian13.yml?label=debian13&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/debian13.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-debian13.json)](https://quay.io/repository/iamenr0s/docker-debian13-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-debian13-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-debian13-ansible) |
| [![fedora37](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/fedora37.yml?label=fedora37&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/fedora37.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-fedora37.json)](https://quay.io/repository/iamenr0s/docker-fedora37-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-fedora37-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-fedora37-ansible) |
| [![fedora38](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/fedora38.yml?label=fedora38&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/fedora38.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-fedora38.json)](https://quay.io/repository/iamenr0s/docker-fedora38-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-fedora38-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-fedora38-ansible) |
| [![fedora39](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/fedora39.yml?label=fedora39&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/fedora39.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-fedora39.json)](https://quay.io/repository/iamenr0s/docker-fedora39-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-fedora39-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-fedora39-ansible) |
| [![fedora40](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/fedora40.yml?label=fedora40&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/fedora40.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-fedora40.json)](https://quay.io/repository/iamenr0s/docker-fedora40-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-fedora40-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-fedora40-ansible) |
| [![fedora41](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/fedora41.yml?label=fedora41&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/fedora41.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-fedora41.json)](https://quay.io/repository/iamenr0s/docker-fedora41-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-fedora41-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-fedora41-ansible) |
| [![fedora42](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/fedora42.yml?label=fedora42&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/fedora42.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-fedora42.json)](https://quay.io/repository/iamenr0s/docker-fedora42-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-fedora42-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-fedora42-ansible) |
| [![fedora43](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/fedora43.yml?label=fedora43&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/fedora43.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-fedora43.json)](https://quay.io/repository/iamenr0s/docker-fedora43-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-fedora43-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-fedora43-ansible) |
| [![fedora44](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/fedora44.yml?label=fedora44&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/fedora44.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-fedora44.json)](https://quay.io/repository/iamenr0s/docker-fedora44-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-fedora44-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-fedora44-ansible) |
| [![rockylinux8](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/rockylinux8.yml?label=rockylinux8&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/rockylinux8.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-rockylinux8.json)](https://quay.io/repository/iamenr0s/docker-rockylinux8-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-rockylinux8-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-rockylinux8-ansible) |
| [![rockylinux9](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/rockylinux9.yml?label=rockylinux9&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/rockylinux9.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-rockylinux9.json)](https://quay.io/repository/iamenr0s/docker-rockylinux9-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-rockylinux9-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-rockylinux9-ansible) |
| [![rockylinux10](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/rockylinux10.yml?label=rockylinux10&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/rockylinux10.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-rockylinux10.json)](https://quay.io/repository/iamenr0s/docker-rockylinux10-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-rockylinux10-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-rockylinux10-ansible) |
| [![ubuntu2204](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/ubuntu2204.yml?label=ubuntu2204&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/ubuntu2204.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-ubuntu2204.json)](https://quay.io/repository/iamenr0s/docker-ubuntu2204-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-ubuntu2204-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-ubuntu2204-ansible) |
| [![ubuntu2404](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/ubuntu2404.yml?label=ubuntu2404&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/ubuntu2404.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-ubuntu2404.json)](https://quay.io/repository/iamenr0s/docker-ubuntu2404-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-ubuntu2404-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-ubuntu2404-ansible) |
| [![ubuntu2604](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/ubuntu2604.yml?label=ubuntu2604&logo=github)](https://github.com/iamenr0s/docker-ansible-images/actions/workflows/ubuntu2604.yml) | [![Quay Pulls](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fiamenr0s%2Fdocker-ansible-images%2Fmain%2Fbadges%2Fquay-ubuntu2604.json)](https://quay.io/repository/iamenr0s/docker-ubuntu2604-ansible) | [![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-ubuntu2604-ansible?logo=docker)](https://hub.docker.com/r/iamenr0s/docker-ubuntu2604-ansible) |

## Features

- **Systemd Services**: The Docker image allows you to manage systemd services inside the container, providing a more comprehensive environment for testing and development.

- **Cgroup Volume**: The image mounts the cgroup volume from the host to the container, ensuring proper functioning of systemd and related services.

- **Ansible Inventory**: An Ansible inventory file is installed within the container at `/etc/ansible/hosts`. This allows you to use Ansible for configuration management tasks.

## Security & Automation

- **Multi-arch builds**: every image is built for `linux/amd64` and `linux/arm64`.
- **Tag-only publishing**: commits to `main` only build the images as a validation check; images are pushed to Docker Hub and Quay (and signed) exclusively when a `v*.*.*` tag is pushed. Each release publishes `latest`, the short commit SHA, and the version as tags.
- **Signed images**: every published digest is signed with [cosign](https://docs.sigstore.dev/) keyless signing using this repository's GitHub Actions OIDC identity — see [Verifying Image Signatures](#verifying-image-signatures).
- **CIS compliance scanning**: a [weekly + on-change workflow](.github/workflows/cis-scan.yml) runs Trivy (vulnerabilities + CIS Docker Benchmark), Dockle, and Hadolint against every image, with findings uploaded to GitHub code scanning. Deliberate deviations required by the systemd test-target use case are documented in [COMPLIANCE.md](COMPLIANCE.md).
- **Automated base image updates**: [Renovate](renovate.json) pins every base image to a digest and raises (auto-merged) PRs when upstream bases are rebuilt, keeping each distro image fresh without ever bumping the distro version itself.
- **Vulnerability reporting**: see [SECURITY.md](SECURITY.md) — GitHub private vulnerability reporting, no public issues for security bugs.

## How to Build the Docker Image

1. Clone this repository to your local machine:

```
git clone https://github.com/iamenr0s/docker-ansible-images.git
```

2. Ensure you have Docker installed on your system.

3. Build the Docker image:
```
docker build -t docker-<DISTRO>-ansible -f <DISTRO>/Dockerfile .
```

## How to Run the Docker Container

To run a container from the built Docker image, use the following command:
```
docker run -d --privileged -v /sys/fs/cgroup:/sys/fs/cgroup:ro docker-<DISTRO>-ansible
```

- The `--privileged` flag is required to run systemd inside the container.
- The `-v` option mounts the host's cgroup volume to the container's cgroup directory.

## Verifying Image Signatures

All images are signed at build time with [cosign](https://docs.sigstore.dev/) keyless signing, using the GitHub Actions OIDC identity of this repository. To verify an image has not been altered:

```
cosign verify \
  --certificate-identity-regexp 'https://github.com/iamenr0s/docker-ansible-images/' \
  --certificate-oidc-issuer https://token.actions.githubusercontent.com \
  docker.io/iamenr0s/docker-<DISTRO>-ansible:latest
```

The same command works against `quay.io/iamenr0s/docker-<DISTRO>-ansible:latest`.

## Important Notes

- Running systemd inside a Docker container is not a typical use case and may have security implications. It is generally recommended to use Docker for stateless services and consider alternative solutions like Kubernetes for managing stateful services with systemd requirements.

- For more information about using this Docker image, refer to the [Docker documentation](https://docs.docker.com/).

## Contributing

Contributions are welcome — see [CONTRIBUTING.md](CONTRIBUTING.md) for the
local pipeline commands and pull request checklist. This project follows the
[Contributor Covenant Code of Conduct](CODE_OF_CONDUCT.md).

## Security

See [SECURITY.md](SECURITY.md) — GitHub private vulnerability reporting, no
public issues for security bugs.

## License

This project is licensed under the [MIT License](LICENSE).
