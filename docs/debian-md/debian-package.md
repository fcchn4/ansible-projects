# Debian Common Packages

This document presents some important details about repository configurations and common package lists.

## List Repositories

- [Debian Sources List](https://wiki.debian.org/SourcesList), with format **deb822**.
- [Debian Multimedia](https://www.deb-multimedia.org/).


## Multimedia Repository non-free
```
deb http://www.deb-multimedia.org buster main non-free
``` 

## Debian Package Base

- Essentials packages for OS.

```text
    linux-headers-$(uname -r)
    build-essential
    checkinstall
    make
    automake
    autoconf
    lsb-release
    dkms
```

- Packages for manage versions.

```text
    git
    gitg
```

- Packages requiered for hardware Intel.

```text
    intel-microcode
    intel-gpu-tools
    inteltool
    lm-sensors
```

Command for **lm-sensors**:

```bash
$ sudo sensor-detect --auto
```

- Packages Firmware

```text
    firmware-linux
    firmware-linux-free
    firmware-linux-nonfree
``` 

- Packages for compress and uncompress.

```text
    bzip2
    zip
    unzip
    rar
    p7zip
    p7zip-full
    p7zip-rar 
    cabextract
    xz-utils
```

- Extra tools.

```text
    whois
    telnet
    vim
    traceroute
    nmap
    bind9utils
    dnsutils
    curl
    wget
    tree
    net-tools
    locales
    htop
    ethtool
    mlocate
    pv
    rsync
```

- Tools for laptop.

```text
    laptop-mode-tools
```

- Required Packages.

```text
    apt-transport-https
    ca-certificates
    gnupg-agent
    software-properties-common
    tuned
    tuned-gtk
    tuned-utils
    hardinfo
    acpi
    acpid
    acpitool
    dirmngr
```

- SSH Server, remote tools.

```text
    ssh
    openssh-server
    openssh-client
    mosh
```

- Firewall.

```text
    ufw
    gufw			
```

- Vitualization.

```text
    qemu-kvm
    qemu-utils
    libvirt-clients
    libvirt-daemon-system
    virt-viewer
    virtinst
    virt-manager
```

Commands for KVM:

```bash
$ sudo adduser $(whoami) libvirt
$ sudo adduser $(whoami) libvirt-qemu
$ sudo adduser $(whoami) kvm
```

- PHP (Optional).

```text
    php
    php-common
    php-pear
    php-gd
    php-cli
    php-curl
    php-mysql
    php-zip
    php-odbc
    php-pgsql
    php-sqlite3
    php-json
    php-readline
    php-gd  
```

- Certificates SSL.

```text
    certbot
```

- Packages for multimedia.

```text
    vlc
    gstreamer1.0-libav
    gstreamer1.0-plugins-ugly
    gstreamer1.0-plugins-bad
    gstreamer1.0-pulseaudio
    vorbis-tools
    faac
    faad
    w64codecs
    ffmpeg
    ffmpeg2theora
```

- Fonts Typographics.

```text
    ttf-mscorefonts-installer
    fonts-freefont-ttf
    fonts-freefont-otf
```

- Graphics Design.

```text
    gimp
    gimp-data-extras
    inkscape
    inkscape-open-symbols
    dia
    dia-rib-network
    dia-shapes
    dia-common
```

- Web Browser Chromium.

```text
    chromium
    chromium-l10n
```

- Additional Packages.

```text
    ghex
    gqrx-sdr
    peek
    stegosuite
    etherape
    ettercap-text-only
    fritzing
    fritzing-parts
    mediainfo
    linkchecker
    testssl.sh
    speedtest-cli
    arduino
    arduino-core
    wireshark
```

- VirtualBox.

URL: [Virtualbox Web](https://www.virtualbox.org/).

- Docker CE.

URL: [Debian Installer](https://docs.docker.com/engine/install/debian/).
