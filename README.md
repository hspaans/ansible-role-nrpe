Role Name
=========

Install and configure NRPE

Requirements
------------

None as the nrpe package is being installed.

Role Variables
--------------

Default variables are set in `defaults/main.yml`.

Dependencies
------------

No dependency on other Ansible Galaxy roles.

Example Playbook
----------------

    - hosts: servers
      vars:
        nrpe_server_allowed_hosts:
          - 10.0.10.0/24
          - 10.0.11.2
          - 127.0.0.1
        nrpe_plugin_packages:
          - nagios-plugins-disk
          - nagios-plugins-nagios
          - nagios-plugins-users
        nrpe_command:
          check_disk_all:
            script: check_disk
            option: -w 80 -c 90
          check_users:
            script: check_users2
            option: -w 1 -c 1
          check_nagios:
            script: check_nagios
            option: -F /var/log/nagios/nagios.log -e 15 -C nagios
      roles:
        - { role: hspaans.nrpe, become: true }

License
-------

MIT

Author Information
------------------

This role was created in 2020 by [Hans Spaans](https://github.com/hspaans).
