FROM python:slim-buster

### -------------------------------------------------
### Metadata information
### -------------------------------------------------
LABEL name="juniper-automation-container"
LABEL maintainer="cremsburg@protonmail.com"
LABEL description="ansible container to manage Juniper devices"
LABEL license="GPLv3"
LABEL url="https://gitlab.com/cremsburg/juniper-automation-container/container_registry"
LABEL build-date="20210321"

### -------------------------------------------------
### Change directory to /home/ansible
### -------------------------------------------------
WORKDIR /home/ansible

### -------------------------------------------------
### Add and install python packages
### -------------------------------------------------
ADD requirements.txt requirements.txt

RUN pip install -r requirements.txt

### -------------------------------------------------
### Install Ansible Galaxy roles and collections
### -------------------------------------------------
RUN ansible-galaxy collection install juniper.device

### -------------------------------------------------
### Copy ansible.cfg to container
### -------------------------------------------------
COPY ansible.cfg /etc/ansible/ansible.cfg

### -------------------------------------------------
### Environmentals
### -------------------------------------------------
ENV ANSIBLE_CONFIG /etc/ansible/ansible.cfg
