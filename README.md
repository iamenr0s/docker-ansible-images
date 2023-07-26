# Docker Ansible Images

This repository contains a Dockerfile and necessary files to build a Docker image based on different operative systems that enables systemd service management, mounts the cgroup volume, and installs an Ansible inventory file.

## Available Images

| Name | Docker Image | Architecture |
|------|--------------|--------------|
|![GitHub Workflow Status (with event)](https://img.shields.io/github/actions/workflow/status/iamenr0s/docker-ansible-images/rockylinux8.yml?label=rockylinux8)|![Docker Pulls](https://img.shields.io/docker/pulls/iamenr0s/docker-rockylinux8-ansible)|amd64,arm64|

## Features

- **Systemd Services**: The Docker image allows you to manage systemd services inside the container, providing a more comprehensive environment for testing and development.

- **Cgroup Volume**: The image mounts the cgroup volume from the host to the container, ensuring proper functioning of systemd and related services.

- **Ansible Inventory**: An Ansible inventory file is installed within the container at `/etc/ansible/hosts`. This allows you to use Ansible for configuration management tasks.

## How to Build the Docker Image

1. Clone this repository to your local machine:

```
git clone https://github.com/iamenr0s/docker-ansible-images.git
cd <DISTRO>
```

2. Ensure you have Docker installed on your system.

3. Build the Docker image:
```
docker build -t docker-<DISTRO>-ansible .
```

## How to Run the Docker Container

To run a container from the built Docker image, use the following command:
```
docker run -d --privileged -v /sys/fs/cgroup:/sys/fs/cgroup:ro docker-<DISTRO>-ansible
```

- The `--privileged` flag is required to run systemd inside the container.
- The `-v` option mounts the host's cgroup volume to the container's cgroup directory.

## Important Notes

- Running systemd inside a Docker container is not a typical use case and may have security implications. It is generally recommended to use Docker for stateless services and consider alternative solutions like Kubernetes for managing stateful services with systemd requirements.

- For more information about using this Docker image, refer to the [Docker documentation](https://docs.docker.com/).

## Issues and Contributions

If you encounter any issues with this Docker image or have suggestions for improvements, please open an issue on the repository.

Contributions in the form of pull requests are also welcome. Feel free to contribute to making these Docker images better!

## License

This project is licensed under the [MIT License](LICENSE).
