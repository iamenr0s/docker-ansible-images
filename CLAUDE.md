# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This repo builds Docker images for Ansible testing across multiple Linux distributions. Each image enables systemd inside Docker (via `--privileged` + cgroup volume mount), installs Ansible via pip in a virtualenv, and places an inventory file at `/etc/ansible/hosts`.

## Build and Run Commands

Build a specific distro image (context is always repo root so `ansible-inventory` is accessible):
```bash
docker build -t docker-<DISTRO>-ansible -f <DISTRO>/Dockerfile .
```

Run with systemd support:
```bash
docker run -d --privileged -v /sys/fs/cgroup:/sys/fs/cgroup:ro docker-<DISTRO>-ansible
```

## Repository Structure

Each distro has its own directory (e.g., `almalinux9/`, `debian12/`, `fedora42/`) containing only a `Dockerfile`. The `ansible-inventory` file at repo root is shared across all images — it's the only non-Dockerfile asset.

Each workflow in `.github/workflows/<distro>.yml` builds and pushes to both Docker Hub (`iamenr0s/docker-<distro>-ansible`) and Quay (`quay.io/iamenr0s/docker-<distro>-ansible`) on version tag pushes (`v*.*.*`), targeting `linux/amd64,linux/arm64`.

## Dockerfile Patterns by Distro Family

**Debian/Ubuntu**: Use `apt-get`, set `ARG DEBIAN_FRONTEND=noninteractive`, install `python3-venv`, `systemd`, `systemd-sysv`. Include `sed` to disable `requiretty` in sudoers.

**RHEL family (AlmaLinux, RockyLinux)**: Use `dnf`, set `ENV PIP_ROOT_USER_ACTION=ignore`, set `ENV container docker`. No systemd unit cleanup needed.

**Fedora**: Same as RHEL family but also requires the aggressive systemd unit cleanup block (removing unwanted `.wants/*` symlinks) because Fedora's systemd is more opinionated.

All images follow this sequence:
1. Install OS packages (including `sudo`, `python3-pip`, build tools)
2. Create virtualenv at `/opt/venv` and activate via `ENV PATH`
3. `pip install ansible cryptography`
4. `mkdir -p /etc/ansible` + `COPY ansible-inventory /etc/ansible/hosts`
5. `VOLUME ["/sys/fs/cgroup"]` + `CMD ["/usr/lib/systemd/systemd"]`

## Adding a New Distro

1. Create `<distro>/Dockerfile` following the appropriate family pattern above.
2. Copy `.github/workflows/almalinux9.yml` (or debian12) as a template, update `IMAGE_NAME` and the `file:` path.
3. Add a row to the README table with the correct workflow filename and image name for the shields.io badges.
