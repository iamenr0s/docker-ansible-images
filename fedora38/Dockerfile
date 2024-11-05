# Use the official Fedoara 38 base image from Quay
FROM quay.io/fedora/fedora:38
LABEL maintainer="iamenr0s"

ENV PIP_ROOT_USER_ACTION=ignore

# Install required packages for Ansible
RUN dnf update -y && \
    dnf install -y python3-pip python3-devel gcc openssl-devel libffi-devel sudo openssh openssh-server && \
    dnf clean all

ENV VIRTUAL_ENV=/opt/venv
RUN python3 -m venv $VIRTUAL_ENV
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

# Install Ansible via pip
RUN pip3 install --no-cache-dir --upgrade pip \
    && pip3 install --no-cache-dir ansible cryptography

# Enable systemd
ENV container docker
RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == systemd-tmpfiles-setup.service ] || rm -f $i; done) && \
    rm -f /lib/systemd/system/multi-user.target.wants/* && \
    rm -f /etc/systemd/system/*.wants/* && \
    rm -f /lib/systemd/system/local-fs.target.wants/* && \
    rm -f /lib/systemd/system/sockets.target.wants/*udev* && \
    rm -f /lib/systemd/system/sockets.target.wants/*initctl* && \
    rm -f /lib/systemd/system/basic.target.wants/* && \
    rm -f /lib/systemd/system/anaconda.target.wants/*

# Ensure /etc/ansible directory exists
RUN mkdir -p /etc/ansible

# Copy the Ansible inventory file to the container
COPY ansible-inventory /etc/ansible/hosts

# Disable requiretty.
RUN sed -i -e 's/^\(Defaults\s*requiretty\)/#--- \1/'  /etc/sudoers

# Start the default target (similar to runlevel 3 in traditional Linux systems)
VOLUME ["/sys/fs/cgroup"]
CMD ["/usr/lib/systemd/systemd"]
