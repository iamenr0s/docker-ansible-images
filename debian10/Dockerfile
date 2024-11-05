# Use the official Debian 10 base image from Docker Hub
FROM debian:buster
LABEL maintainer="iamenr0s"

ARG DEBIAN_FRONTEND=noninteractive

# Install required packages for Ansible
RUN apt-get update && apt-get install -y --no-install-recommends \
       sudo systemd systemd-sysv build-essential wget libffi-dev libssl-dev procps \
       python3-pip python3-dev python3-setuptools python3-wheel python3-apt python3-venv \
       libc6 openssh-server \
    && rm -rf /var/lib/apt/lists/* \
    && rm -Rf /usr/share/doc && rm -Rf /usr/share/man \
    && apt-get clean

ENV VIRTUAL_ENV=/opt/venv
RUN python3 -m venv $VIRTUAL_ENV
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

# Install Ansible via pip
RUN pip3 install --no-cache-dir --upgrade pip \
    && pip3 install --no-cache-dir ansible cryptography

# Ensure /etc/ansible directory exists
RUN mkdir -p /etc/ansible

# Copy the Ansible inventory file to the container
COPY ansible-inventory /etc/ansible/hosts

# Disable requiretty.
RUN sed -i -e 's/^\(Defaults\s*requiretty\)/#--- \1/'  /etc/sudoers

# Start the default target (similar to runlevel 3 in traditional Linux systems)
VOLUME ["/sys/fs/cgroup"]
CMD ["/lib/systemd/systemd"]
