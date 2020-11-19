ansible-role-open-port
======================

[![Ansible Role: bit_kitchen.open_port](https://img.shields.io/ansible/role/51886.svg)](https://galaxy.ansible.com/bit_kitchen/open_port)
[![Build Status](https://travis-ci.org/bit-kitchen/ansible-role-open-port.svg?branch=master)](https://travis-ci.org/bit-kitchen/ansible-role-open-port)

An ansible role that opens port in firewalld and/or GCP Firewall.

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
**GCP firewall variables (optional)** | | The following applies to GCP only.
gcp_project               | undefined | If undefined and running on GCP, value will be read from metadata server.
gcp_service_account_email | undefined | If undefined and running on GCP, value will be read from metadata server.
gcp_rule_name             | 'port-' + open_port + '-' + open_protocol | GCP Firewall rule name.
gcp_rule_description      | gcp_rule_name | GCP Firewall rule description.

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

  # Open 80/tcp and configure GCP Firewall using machine account read from
  # metadata server, and specify rule name and description explicitly.
  - role: bit_kitchen.port
    open_port: 80
    open_protocol: tcp
    gcp_rule_name: web
    gcp_rule_description: Allow http traffic.

  # Open 443/tcp and configure GCP Firewall using explicitly specified project
  # and account.
  - role: bit_kitchen.port
    open_port: 443
    open_protocol: tcp
    gcp_project: my-project-name
    gcp_service_account_email: 77665544321-compute@developer.gserviceaccount.com
```

License
-------

[MIT](LICENSE)

Author Information
------------------

[bit.kitchen](https://github.com/bit-kitchen)
