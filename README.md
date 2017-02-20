[![Build Status](https://travis-ci.org/bashrc666/ansible-check_oracle_health.svg?branch=master)](https://travis-ci.org/bashrc666/ansible-check_oracle_health)

Ansible-check_oracle_health
=========

This role is used to deploy the check_oracle_health script for nrpe monitoring

Requirements
------------

 - Ansible >= 1.9
 - `epel-release` on remote server
 - `Oracle12c` on remote server
 - `CentOS 7` on remote server

Role Variables
--------------

```
oracle_monitoring_user: C##nagios
oracle_monitoring_passwd: supervision
oracle_health_name: check_oracle_health-3.0.1
oracle_health_repo: "https://labs.consol.de/assets/downloads/nagios/{{ oracle_health_name}}.tar.gz"
oracle_env_path: /home/oracle/.profile
```

Dependencies
------------

 - ansible-nagios-nrpe-server

Example Playbook
----------------

```
- hosts: oracle12c
  roles:
    - nrpe-server
    - ansible-check_oracle_health
  vars:
    nagios_nrpe_server_plugins_dir: /usr/lib64/nagios/plugins
    nagios_nrpe_server_allowed_hosts: ["X.X.X.X"]
    nagios_nrpe_command:
      oracle_tnsping:
        script: check_oracle_health
        option: --mode --connect $ARG1$ --username $ARG2$ --password $ARG3$ tnsping
      oracle_connection-time:
        script: check_oracle_health
        option: --connect $ARG1$ --username $ARG2$ --password $ARG3$ --mode connection-time
      oracle_sga-data-buffer-hit:
        script: check_oracle_health
        option: --connect $ARG1$ --username $ARG2$ --password $ARG3$ --mode sga-data-buffer-hit-ratio
    oracle_monitoring_user: C##nagios
    oracle_monitoring_passwd: supervision
    nagios_nrpe_server_dont_blame_nrpe: 1
```

License
-------

BSD

Author Information
------------------

Gregory O'Toole / Capensis
