[![No Maintenance Intended](http://unmaintained.tech/badge.svg)](http://unmaintained.tech/)

ufw
===

[![Build Status](https://travis-ci.org/kbrebanov/ansible-ufw.svg?branch=master)](https://travis-ci.org/kbrebanov/ansible-ufw)

Installs and configures ufw

Requirements
------------

This role requires Ansible 1.9 or higher.

Role Variables
--------------

| Name                | Default                                                  | Description                                         |
|:--------------------|:---------------------------------------------------------|:----------------------------------------------------|
| ufw_incoming_policy | "deny"                                                   | Set default incoming policy (allow, deny or reject) |
| ufw_ipv6            | "yes"                                                    | Enable or disable support for IPv6                  |
| ufw_logging         | "off"                                                    | Enable or disable logging                           |
| ufw_outgoing_policy | "allow"                                                  | Set default outgoing policy (allow, deny or reject) |
| ufw_routed_policy   | "deny"                                                   | Set default routed policy (allow, deny or reject)   |
| ufw_rules           | [{rule: "allow", proto: "tcp", src: "any", to_port: 22}] | List of rules                                       |

Dependencies
------------

None

Example Playbook
----------------

Install ufw and allow SSH from anywhere
```
- hosts: all
  roles:
    - kbrebanov.ufw
```

Install ufw, allow SSH and HTTPS from anywhere and disable IPv6 support
```
- hosts: all
  vars:
    ufw_ipv6: "no"
    ufw_rules:
      - rule: "allow"
        proto: "tcp"
        src: "any"
        to_port: 22
      - rule: "allow"
        proto: "tcp"
        src: "any"
        to_port: 443
  roles:
    - kbrebanov.ufw
```

License
-------

BSD

Author Information
------------------

Kevin Brebanov
