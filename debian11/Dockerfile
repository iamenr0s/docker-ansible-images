# Use the official Debian 11 base image from Docker Hub
FROM debian:bullseye@sha256:6f519a81440354a85eb592c5f32109ab80605f6b892455983a6f618bf87fabe9
LABEL maintainer="iamenr0s"

ARG DEBIAN_FRONTEND=noninteractive

# Update sources.list to use archive.debian.org since Debian 11 is EOL.
# bullseye-security was never mirrored to archive.debian.org (its fixes
# are already folded into the point-release bullseye archive), so only
# the main suite is needed here.
RUN echo "deb http://archive.debian.org/debian/ bullseye main contrib non-free" > /etc/apt/sources.list && \
    echo "Acquire::Check-Valid-Until \"false\";" > /etc/apt/apt.conf.d/10no-check-valid-until

# Install required packages for Ansible. Upgrade first: the base image
# predates the final bullseye point release archived here, and installing
# -dev packages otherwise fails on exact-version pins (e.g. libc6-dev
# against the now-unavailable older libc6 build baked into the image).
RUN apt-get -o Acquire::AllowInsecureRepositories=true update && apt-get upgrade -y --allow-unauthenticated && apt-get install -y --no-install-recommends --allow-unauthenticated \
       sudo systemd systemd-sysv build-essential wget libffi-dev libssl-dev procps \
       python3-pip python3-dev python3-setuptools python3-wheel python3-apt python3-venv \
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
