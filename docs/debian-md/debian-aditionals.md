# Optional Packages

- KVM

Install Packages:

```yml
  - name: KVM VIRTUALIZATION
    apt:
      name:
        - qemu-kvm
        - qemu-utils
        - libvirt-clients
        - libvirt-daemon-system
        - virt-viewer
        - virt-what
        - virtinst
        - virt-manager
      state: latest
```

Enable Libvirt Daemon:

```bash
  - name: ENABLE DAEMON LIBVIRT
    systemd:
      name: libvirtd
      state: started
      enabled: yes
```

Add current user to group:

```yml
  - name: ADD USER ON GROUPS
    user:
      name: "{{ debian_user }}"
      groups: kvm,libvirt,libvirt-qemu
      append: yes
```

- Docker Compose Binary

Create a variable:

```yml
    vars:
      ...
      docker_compose_version: v2.5.0
```

Tasks for Debian Desktop

```yml
  - name: GET KERNEL NAME
    shell: uname -s
    register: kernel_name_output

  - debug: msg="{{ kernel_name_output.stdout }}"

  - name: GET HARDWARE MACHINE
    shell: uname -m
    register: kernel_machine_output

  - debug: msg="{{ kernel_machine_output.stdout }}"

  - name: INSTALL DOCKER COMPOSE
    get_url:
      url: https://github.com/docker/compose/releases/download/{{ docker_compose_version }}/docker-compose-{{ kernel_name_output.stdout }}-{{ kernel_machine_output.stdout }}
      dest: /usr/local/bin/docker-compose 
      mode: "0755"
```

- TCPDUMP and WIRESHARK GROUPS

```yml
  - name: ADD USER ON GROUPS
    user:
      name: "{{ debian_user }}"
      groups: tcpdump,wireshark
      append: yes
```
