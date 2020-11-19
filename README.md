ansible-role-open-port
======================

[![Ansible Role: bit_kitchen.open_port](https://img.shields.io/ansible/role/51886.svg)](https://galaxy.ansible.com/bit_kitchen/open_port)
[![Build Status](https://travis-ci.org/bit-kitchen/ansible-role-open-port.svg?branch=master)](https://travis-ci.org/bit-kitchen/ansible-role-open-port)

An ansible role that opens port in firewalld.

Note: chances are you need to connect as root or use *become* to use this role.

    ansible-galaxy install bit_kitchen.open_port

Requirements
------------

None.

Role Variables
--------------

variable      | default   | Note
------------- | --------- | ----
open_port     | undefined | Specify a port or this role will be a no-op.
open_protocol | undefined | Specify "tcp" or "udp", defaults to both.

Dependencies
------------

None.

Example Playbook
----------------

```yml
- hosts: servers
  roles:
  # Open 80/tcp
  - role: bit_kitchen.port
    open_port: 80
    open_protocol: tcp

  # Open 53/udp
  - role: bit_kitchen.port
    open_port: 53
    open_protocol: udp

  # Open 443/tcp and 443/udp
  - role: bit_kitchen.port
    open_port: 443

  # Do nothing
  - role: bit_kitchen.port
```

License
-------

[MIT](LICENSE)

Author Information
------------------

[bit.kitchen](https://github.com/bit-kitchen)
