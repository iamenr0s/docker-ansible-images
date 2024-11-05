# Use the official Alma Linux 9 base image from Quay
FROM quay.io/almalinuxorg/9-base:9
LABEL maintainer="iamenr0s"

ENV PIP_ROOT_USER_ACTION=ignore

# Install required packages for Ansible
RUN dnf update -y && \
    dnf install -y sudo python3-pip python3-devel gcc openssl-devel libffi-devel && \
    dnf clean all

ENV VIRTUAL_ENV=/opt/venv
RUN python3 -m venv $VIRTUAL_ENV
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

# Install Ansible via pip
RUN pip3 install --no-cache-dir --upgrade pip \
    && pip3 install --no-cache-dir ansible cryptography

# Enable systemd
ENV container docker

# Ensure /etc/ansible directory exists
RUN mkdir -p /etc/ansible

# Copy the Ansible inventory file to the container
COPY ansible-inventory /etc/ansible/hosts

# Start the default target (similar to runlevel 3 in traditional Linux systems)
VOLUME ["/sys/fs/cgroup"]
CMD ["/usr/lib/systemd/systemd"]
