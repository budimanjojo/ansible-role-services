Ansible Services Role
=====================

Role to manage linux services.

Supported OS Families
---------------------

- Ubuntu (tested)
- Arch Linux (tested)
- Redhat (tested)
- Other Linux distributions should work just fine

Role Variables
--------------

Available variables are listed below:
```
## Dict of services to manage based on OS
services_list:
  all:
  - name: name of service (string)
    state: state of service, choices are 'stopped', 'started', 'reloaded', 'restarted' (string)
    enabled: whether the service should start on boot (bool)
  # same as above
  debian: []
  archlinux: []
  redhat: []
```

Dependencies
------------

None

Example Playbook
----------------

Here is an example playbook:
```
- hosts: all

  vars:
    services_list:
      all:
      - name: haproxy
        state: started
        enabled: true
      - name: keepalived
        state: restarted
      debian:
      - name: apache2
        state: stopped
        enabled: false
      archlinux:
      - name: httpd
        state: stopped
        enabled: false
      redhat:
      - name: httpd
        state: stopped
        enabled: false

  roles:
  - budimanjojo.services
```

License
-------

MIT License
