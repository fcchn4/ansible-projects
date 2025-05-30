# Ansible Install Linux

This repository contains a list of packages for Fedora, Debian, and Ubuntu distributions. It only contains a long list of packages for some GNU/Linux distributions.

## Pre-Requisites

First we must manually execute the following commands on the computer where the installation will take place:

```bash
$ sudo apt update
$ sudo apt install -y openssh-server
$ sudo systemctl enable --now sshd.service
```

Then we must copy a public SSH key on the computer where the installations will be executed:

```bash
$ ssh-copy-id -o PubkeyAuthentication=no -i ~/.ssh/demo-ssh.pub user_name@ip_address_or_localhost
```

This ansible poroject is for automatic install on post-installation for Ubuntu Operating System.

## Config Files and replace values

The project have three playbooks:

- ubuntu-base.yml
- ubuntu-desktop.yml
- ubuntu-devops.yml

## Commands

First we are located on the route:

```bash
$ cd ubuntu-os
```

Execution order:

1. **ubuntu-base.yml**:

```bash
$ ansible-playbook ubuntu-base.yml \
--ask-become-pass \
-i inventory/inventory.yml \
-e "ansible_python_interpreter=/usr/bin/python3"
```

2. **ubuntu-desktop.yml**:

```bash
$ ansible-playbook ubuntu-desktop.yml \
--ask-become-pass \
-i inventory/inventory.yml \
-e "ansible_python_interpreter=/usr/bin/python3"
```

3. **ubuntu-devops.yml**:

```bash
$ ansible-playbook ubuntu-devops.yml \
--ask-become-pass \
-i inventory/inventory.yml \
-e "ansible_python_interpreter=/usr/bin/python3"
```
