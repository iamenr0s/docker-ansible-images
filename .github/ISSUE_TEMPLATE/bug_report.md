---
name: Bug report
about: Report a problem with one of the images
title: ''
labels: bug
assignees: ''
---

## Describe the bug

A clear and concise description of what the bug is.

## To reproduce

How you ran the image:

```bash
docker run -d --privileged -v /sys/fs/cgroup:/sys/fs/cgroup:ro iamenr0s/docker-<distro>-ansible:latest
```

## Expected behavior

What you expected to happen.

## Actual behavior

What actually happened. Include relevant container logs (`docker logs <container>`):

```
paste output here
```

## Environment

- Image and tag (e.g. `iamenr0s/docker-debian12-ansible:latest`):
- Registry (Docker Hub / Quay):
- Architecture (amd64 / arm64):
- Host OS and Docker/Podman version:

## Additional context

Anything else that might help (molecule scenario, cgroup version, rootless vs rootful, etc.).
