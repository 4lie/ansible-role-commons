# Commons Ansible Role

An Ansible Role for configuring Debian like systems.

## Installation

``` yaml
# requirements.yaml
- src: git@github.com:4lie/ansible-role-commons.git
  scm: git
  version: master
  name: commons
```

``` bash
ansible-galaxy install -r requirements.yaml
```

## Role Variables

``` yaml
# Update apt Packages
apt_update: 'true'

# Timezone
timezone: Asia/Tehran

# Sysfs Configs
sysfs_config_file: /etc/sysfs.conf
sysfs_config: []

# List of Basic Packages
default_pkgs:
  - apt-transport-https
  - bridge-utils
  - conntrack
  - curl
  - dstat
  - git
  - htop
  - ifenslave
  - iftop
  - iptables
  - iptables-persistent
  - iptraf
  - jq
  - ncdu
  - python-apt
  - python-pip
  - screen
  - sudo
  - sysfsutils
  - sysstat
  - telnet
  - tmux
  - vim
  - unzip
  - dnsutils
  - python-jmespath

# List OF Kernel Modules
basic_modprobe:
  - bonding
  - ip_conntrack
  - nf_conntrack

# DNS resolv.conf
resolv_search: ''
resolv_domain: ''
resolv_nameservers:
  - 4.2.2.4
  - 8.8.8.8
resolv_sortlist: ''
resolv_options:
  - timeout:2

# Sysctl
sysctl_config:
  vm.swappiness: 1
  net.ipv4.tcp_tw_reuse: 1
  net.core.somaxconn: 50000
  net.ipv4.tcp_fin_timeout: 15
  fs.file-max: 1024000
  fs.nr_open: 1024000
  net.ipv4.tcp_max_tw_buckets: 1440000
  net.ipv4.ip_local_port_range: 15000 65000
  net.ipv4.tcp_window_scaling: 1
  net.ipv4.tcp_adv_win_scale: 1
  net.ipv4.tcp_max_syn_backlog: 240000
  net.core.optmem_max: 2516582
  net.core.netdev_max_backlog: 60000
  net.core.netdev_budget: 1200
  net.nf_conntrack_max: 450000
  vm.dirty_ratio: 10
  vm.dirty_background_ratio: 2

# Limits
limits_config:
  root_hard:
    domain: root
    limit_type: hard
    limit_item: nofile
    value: 1024000
  root_soft:
    domain: root
    limit_type: soft
    limit_item: nofile
    value: 1024000
```

## Example Playbook

``` yaml
- hosts: servers
  roles:
    - commons
```
