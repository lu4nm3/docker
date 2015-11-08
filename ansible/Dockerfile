FROM ubuntu:14.04
MAINTAINER Luis Medina <luis@escala.io>

# Create ansible user and group.
RUN adduser --disabled-password --gecos '' --shell /bin/bash ansible && \
    adduser ansible sudo && \
    grep -q "%sudo ALL=(ALL) NOPASSWD:ALL" /etc/sudoers || echo "\n%sudo ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Install necessary packages.
RUN apt-get -y update && \
    apt-get install -y git python-httplib2 python-jinja2 python-keyczar python-paramiko python-pip python-pkg-resources python-setuptools python-yaml && \
    pip install boto

# Download Ansible.
RUN mkdir /opt/ansible/ && \
    git clone git://github.com/ansible/ansible.git --recursive /opt/ansible/ansible

# Set up Ansible environment variables.
ENV PATH /opt/ansible/ansible/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ENV PYTHONPATH /opt/ansible/ansible/lib
ENV ANSIBLE_LIBRARY /opt/ansible/ansible/library
ENV MANPATH /opt/ansible/ansible/docs/man

USER ansible
RUN ssh-keygen -q -t rsa -N '' -f /home/ansible/.ssh/id_rsa
WORKDIR /home/ansible