# Optional Repository List

- OpenVPN3 Client

Package native on Debian repositories: openvpn3-client

```yaml
    - name: ADD OPENVPN3 SOURCES
      deb822_repository:
        name: openvpn3
        types: deb
        uris: https://packages.openvpn.net/openvpn3/debian
        suites: "{{ debian_version }}"
        signed_by: https://packages.openvpn.net/packages-repo.gpg
        enabled: true
        components:
          - main
```

- Azure CLI

```yaml
    - name: AZURE-CLI
      deb822_repository:
        name: azure-cli
        types: deb
        uris: https://packages.microsoft.com/repos/azure-cli
        suites: "{{ debian_version }}"
        signed_by: https://packages.microsoft.com/keys/microsoft.asc
        enabled: true
        architectures:
          - amd64
        components:
          - main
```

- Syncthing

```yaml
    - name: SYNCTHING
      deb822_repository:
        name: sincthing
        types: deb
        uris: https://apt.syncthing.net
        suites: syncthing
        signed_by: https://syncthing.net/release-key.gpg
        enabled: true
        components:
          - stable
```

- Signal

```yaml
    - name: ADD SIGNAL SOURCES
      deb822_repository:
        name: signal
        types: deb
        uris: https://updates.signal.org/desktop/apt
        suites: xenial
        signed_by: https://updates.signal.org/desktop/apt/keys.asc
        enabled: true
        architectures: amd64
        components: main
```

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
