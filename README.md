![Ansible Lint](https://github.com/johanneskastl/ansible-role-caddy_server/workflows/Ansible%20Lint/badge.svg)

caddy_server
=========

Install and configure a caddy webserver

Requirements
------------

None.

Role Variables
--------------

By default this role will install Caddy and create a simple `Caddyfile`, that
only shows a greeting:

```
Hello from the caddy_server ansible role!
```

You can configure Caddy by specifying the complete `Caddyfile` content in the
variable `caddy_config`. Check the example playbooks below for details.

Dependencies
------------

None

Example Playbook using the default caddy configuration
----------------

    - hosts: servers
      roles:
        - role: 'johanneskastl.caddy_server'

Example Playbook setting a special caddy configuration
----------------

    - hosts: servers
      roles:
        - role: 'johanneskastl.caddy_server'
          caddy_config: |
            http://{{ hostvars[inventory_hostname]['ansible_default_ipv4']['address'] }}:8080
            respond /* 200 {
                body "I wanted to have a different message shown...
            "
                close
            }

License
-------

BSD-3-Clause

Author Information
------------------

I am Johannes Kastl, reachable via kastl@b1-systems.de.
