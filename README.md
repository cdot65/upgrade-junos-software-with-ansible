# Ansible example: Upgrade JunOS Software

[![N|Solid](https://upload.wikimedia.org/wikipedia/commons/3/31/Juniper_Networks_logo.svg)](https://junos-ansible-modules.readthedocs.io/en/stable/)

## Overview

This example will show how to use Ansible to upgrade your Juniper network devices.

In addition to the Ansible playbok, this project also ships with additional tools to help you along your way. You will find a Dockerfile for running the project in an isolated environment, and an Invoke tasks file for those of us that hate typing out everything all the time.

## ⚙️ `How it works`

Ansible will build a NETCONF session to the device and manage the upload / upgrade process. In this example, a web server running NGINX is hosting the image.

Let's take a second to review the documentation in the `files/docs/` directory.

Name | Description
---- | -----------
[Ansible Playbook](files/docs/pb.junos.upgrade.yaml.rst) | Upgrade a network device
[NGINX setup](files/docs/nginx.rst) | NGINX overview (optional)
[Inventory file](files/docs/inventory.rst) | Inventory

## 📝 `Dependencies`

Refer to the Poetry Lock file located at [poetry.lock](poetry.lock) for detailed descriptions on each package installed.

## 🚀 `Executing the playbook`

This project provides two unique methods of executing the playbook:

[Executing with Docker](files/docs/execute_with_docker.rst) | Execute with Docker

[Executing with Python](files/docs/execute_with_python.rst) | Execute with Python

## Note for Ansible Tower / AWX users

You'll note that there is an ansible.cfg file found in the root of the project's directory, the only purpose this serves is for Ansible Tower / AWX, which will look for these files when the project syncs from Gitlab/Github/Whatever, and Tower will auto-install the packages.

The ansible.cfg file will be the definitive for each Playbook (Template) execution, so super important to keep it here.
