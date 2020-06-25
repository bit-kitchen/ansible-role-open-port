ansible-role-open-port
======================

An ansible role that opens port in firewalld.

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
