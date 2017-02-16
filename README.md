[![Build Status](https://travis-ci.org/bashrc666/ansible-check_oracle_health.svg?branch=master)](https://travis-ci.org/bashrc666/ansible-check_oracle_health)

Ansible-check_oracle_health
=========

A brief description of the role goes here.

Requirements
------------

epel-release

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

Ensure Oracle env vars are set for root !

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

# TODO

```
chmod 664 /oracle/app/oracle/product/12.1.0/dbhome_1/network/admin/tnsnames.ora

[root@oracle12c ~]# cat /etc/sysconfig/nrpe 
# specify additional command line arguments for nrpe
NRPE_SSL_OPT=""
ORACLE_BASE=/oracle/app/oracle
ORACLE_HOME=/oracle/app/oracle/product/12.1.0/dbhome_1
PATH=/oracle/app/oracle/product/12.1.0/dbhome_1/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin
LD_LIBRARY_PATH=/oracle/app/oracle/product/12.1.0/dbhome_1/lib:/lib:/usr/lib:/usr/lib64
CLASSPATH=/oracle/app/oracle/product/12.1.0/dbhome_1/jlib:/oracle/app/oracle/product/12.1.0/dbhome_1/rdbms/jlib
```

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
