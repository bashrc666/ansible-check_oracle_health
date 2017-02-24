[![Build Status](https://travis-ci.org/bashrc666/ansible-check_oracle_health.svg?branch=master)](https://travis-ci.org/bashrc666/ansible-check_oracle_health)

Ansible-check_oracle_health
=========

This role is used to deploy the check_oracle_health script for local or nrpe monitoring

Requirements
------------

 - Ansible >= 1.9
 - epel-release
 - CentOS 7

Role Variables
--------------

```
# defaults file for ansible-check_oracle_health
nagios_nrpe_server_plugins_dir: /usr/lib64/nagios/plugins/
oracle_health_name: check_oracle_health-3.0.1
oracle_health_repo: "https://labs.consol.de/assets/downloads/nagios/{{ oracle_health_name}}.tar.gz"
oracle_env_path: /home/oracle/.profile
nrpe_ssl_opt: ""
check_oracle_health_system_group: nagios
check_oracle_health_system_owner: nagios
check_oracle_health_env_oracle:
  ORACLE_HOME: /usr/lib/oracle/12.1/client64/lib
  LD_LIBRARY_PATH: /usr/lib/oracle/12.1/client64/lib/
  PATH: /sbin:/bin:/usr/sbin:/usr/bin:/usr/lib/oracle/12.1/client64/bin
# Provide check_oracle_health_over_nrpe to true if you want to install as a nrpe check
check_oracle_health_over_nrpe: false
check_oracle_health_env_path: /root/.bashrc
```

Dependencies
------------

Depence of wich case of install you want:
 - with nrpe on oracle server:
    - add role nagios-nrpe-server
    - set `check_oracle_health_over_nrpe: true`
    - overide default vars to your case
 
 - remote or local install without nrpe:
    - None
  

Example Playbook
----------------

Simple and remote install:

```
- hosts: monitoring
  roles:
    - ansible-check_oracle_health
  vars:
    # override default vars to your case
```

Remote install on oracle server:

```
- hosts: monitoring
  roles:
    - ansible-check_oracle_health
  vars:
    check_oracle_health_over_nrpe: true
    nagios_nrpe_server_plugins_dir: /usr/lib64/nagios/plugins/
    check_oracle_health_system_group: nagios
    check_oracle_health_system_owner: nagios
    check_oracle_health_env_path: /home/oracle/.profile
```

License
-------

BSD

Author Information
------------------

Gregory O'Toole / Capensis
