# OpenSSH for BCLinux R8

## Files

```plain
├── RPMS
│   └── x86_64
│       ├── openssh-9.8p1-1.el8.bclinux.x86_64.rpm
│       ├── openssh-askpass-9.8p1-1.el8.bclinux.x86_64.rpm
│       ├── openssh-askpass-debuginfo-9.8p1-1.el8.bclinux.x86_64.rpm
│       ├── openssh-askpass-gnome-9.8p1-1.el8.bclinux.x86_64.rpm
│       ├── openssh-askpass-gnome-debuginfo-9.8p1-1.el8.bclinux.x86_64.rpm
│       ├── openssh-clients-9.8p1-1.el8.bclinux.x86_64.rpm
│       ├── openssh-clients-debuginfo-9.8p1-1.el8.bclinux.x86_64.rpm
│       ├── openssh-debuginfo-9.8p1-1.el8.bclinux.x86_64.rpm
│       ├── openssh-debugsource-9.8p1-1.el8.bclinux.x86_64.rpm
│       ├── openssh-server-9.8p1-1.el8.bclinux.x86_64.rpm
│       └── openssh-server-debuginfo-9.8p1-1.el8.bclinux.x86_64.rpm
├── SOURCES
│   ├── openssh-9.8p1.tar.gz
│   └── x11-ssh-askpass-1.2.4.1.tar.gz
├── SPECS
│   └── openssh.spec
└── SRPMS
    └── openssh-9.8p1-1.el8.bclinux.src.rpm
```

## Install

### Backup config

```shell
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.$(date +'%Y%m%d')
```

### Update package

```shell
sudo rpm -Uvh openssh-9.8p1-1.el8.bclinux.x86_64.rpm openssh-clients-9.8p1-1.el8.bclinux.x86_64.rpm openssh-server-9.8p1-1.el8.bclinux.x86_64.rpm -y
```

or

```shell
sudo dnf localinstall openssh-9.8p1-1.el8.bclinux.x86_64.rpm openssh-clients-9.8p1-1.el8.bclinux.x86_64.rpm openssh-server-9.8p1-1.el8.bclinux.x86_64.rpm -y
```

### Verify 

```shell
ssh -V
rpm -qa | grep openssh
```

Result: 
```plain
OpenSSH_9.8p1, without OpenSSL

openssh-9.8p1-1.el8.bclinux.x86_64
openssh-server-9.8p1-1.el8.bclinux.x86_64
openssh-clients-9.8p1-1.el8.bclinux.x86_64
```

### Restart service

```shell
sudo chmod 0600 /etc/ssh/ssh_host_*_key
sudo systemctl restart sshd
sudo systemctl status sshd
```

## Build

[Gist: FalconIA/BCLinux-R8-OpenSSH.md](https://gist.github.com/FalconIA/42d7b44ff3872be32e946de7182c21c4/3ac87e1a94fe63358f8138d08e63ee343d966167)
