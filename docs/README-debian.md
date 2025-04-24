# Ansible Install Linux

This repository contains a list of packages for Debian. It only contains a long list of packages for some GNU/Linux distributions.

## List

- [Debian Packages](docs/debian-package.md)
- [Extra Packages](docs/extra-package.md)
- [Ansible Code Snippets](docs/package-install.md)

## Pre-Requisites

First we must manually execute the following commands on the computer where the installation will take place:

```bash
$ su -c "vim.tiny /etc/group"       # Add user name in sudo group: "sudo:x:27:user_name"
$ su -c "systemctl enable --now sshd.service"
```

Then we must copy a public SSH key on the computer where the installations will be executed:

```bash
$ ssh-copy-id -o PubkeyAuthentication=no -i ~/.ssh/demo-ssh.pub user_name@ip_address_or_localhost
```

This ansible poroject is for automatic install on post-installation for Debian Operating System.

## Config Files and replace values

The project have three playbooks:

- debian-base.yml
- debian-desktop.yml
- debian-security.yml

## Versions

- XFCE: 4.18
- Debian: 12 Bookworm
- Ansible: 2.16

## Commands

First we are located on the route:

```bash
$ cd ansible-debian
```

Execution order:

1. **debian-base.yml**:

```bash
$ ansible-playbook debian-base.yml --ask-become-pass \
-i inventory/inventory.yml
```

2. **debian-desktop.yml**:

```bash
$ ansible-playbook debian-desktop.yml -i inventory/inventory.yml
```

3. **debian-security.yml**:

```bash
$ ansible-playbook debian-security.yml -i inventory/inventory.yml
```

4. **debian-xfce4.yml**:

```bash
$ ansible-playbook debian-xfce4.yml -i inventory/inventory.yml
```

## Example Commands

- Execute ansible playbook commands as sudo (--ask-become-pass or -k):

```bash
$ ansible-playbook debian-base.yml -i inventory.yml -k
```

- Execute ansible playbook with reference python version:

```bash
$ ansible-playbook debian-security.yml -i inventory.yml \
-e "ansible_python_interpreter=/usr/bin/python3" --ask-become-pass
```
