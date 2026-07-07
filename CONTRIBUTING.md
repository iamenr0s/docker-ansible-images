# Contributing

Thanks for taking the time to contribute to `docker-ansible-images`!

## Getting started

1. Fork the repository and create your branch from `main`.
2. You need Docker or Podman installed locally.

## Making changes

- Keep changes small and focused — one topic per pull request.
- Each distro lives in its own directory containing only a `Dockerfile`; the shared `ansible-inventory` file at the repo root is copied into every image.
- Follow the existing Dockerfile pattern for the distro family (Debian/Ubuntu, RHEL family, Fedora) — see `CLAUDE.md` for the family-specific notes.

## Testing

Before opening a pull request, make sure the affected image builds and boots systemd (build context is always the repo root):

```bash
docker build -t docker-<distro>-ansible -f <distro>/Dockerfile .
docker run -d --privileged -v /sys/fs/cgroup:/sys/fs/cgroup:ro docker-<distro>-ansible
docker exec <container> ansible --version
```

CI builds every image for `linux/amd64` and `linux/arm64` — changes must not break either architecture.

## Submitting a pull request

1. Ensure the affected image(s) build locally.
2. Fill in the pull request template.
3. A maintainer will review your PR; CI must be green before merge.

## Reporting bugs and requesting features

Use the issue templates — they ask for the details (image, tag, architecture) needed to reproduce a problem.

## Code of Conduct

This project follows the [Contributor Covenant Code of Conduct](CODE_OF_CONDUCT.md). By participating you agree to abide by it.
