ansible-role-network
=========
[![Build Status](https://travis-ci.org/t2d/ansible-role-network.svg?branch=master)](https://travis-ci.org/t2d/ansible-role-network)
[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-network-blue.svg)](https://galaxy.ansible.com/t2d/network/)

Configure network interfaces with multi-line strings

Role Variables
--------------

```
network_interfaces: undefined  # Set to configure in /etc/network/interfaces
network_interfaces_d: {}  # Set to configure in /etc/network/interfaces.d
```

Download
--------

Download latest release with `ansible-galaxy`

```
ansible-galaxy install t2d.network
```

Example Playbook
----------------

```
- hosts: bridged
  roles:
    - t2d.network
  vars:
    network_interfaces: |
      iface eno3 inet manual

      auto bridge
      iface bridge inet static
        bridge_ports eno3
        bridge_stp off       
        bridge_waitport 0    
        bridge_fd 0          
        address 0.0.0.0

- hosts: vm
  roles:
    - t2d.network
  vars:
    network_interfaces_d:
      ens8: |
        auto ens8
        iface ens8 inet static
          address 192.168.0.2/24
          gateway 192.168.0.1
```

License
-------

GPLv3

