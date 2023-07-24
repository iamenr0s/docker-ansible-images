# Use the official Rocky Linux 8 base image from Docker Hub
FROM rockylinux/rockylinux:8
LABEL maintainer="enr0s"

# Install required packages for Ansible
RUN dnf update -y && \
    dnf install -y python3-pip python3-devel gcc openssl-devel libffi-devel && \
    dnf clean all

# Install Ansible via pip
RUN pip3 install --upgrade pip && \
    pip3 install ansible

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

# Copy the Ansible inventory file to the container
COPY ../ansible_inventory /etc/ansible/hosts

# Disable requiretty.
RUN sed -i -e 's/^\(Defaults\s*requiretty\)/#--- \1/'  /etc/sudoers

# Start the default target (similar to runlevel 3 in traditional Linux systems)
VOLUME ["/sys/fs/cgroup"]
CMD ["/usr/lib/systemd/systemd"]
