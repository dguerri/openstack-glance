Glance
=========

OpenStack Glance image service installation

_Tested on Ubuntu Precise (12.04) and Trusty (14.04)_

Requirements
------------

A MySQL server. See `mysql_hostname`, `mysql_admin_username` and
`mysql_rootpass` below.

A RabbitMQ server. See `rabbit_hostname`, `rabbit_username` and
`rabbit_pass` below.

A Keystone server. See `keystone_hostname`, `keystone_admin_port` and
`admin_token` below.


Role Variables
--------------

# Other systems/services
* `keystone_hostname`:    Hostname/IP address where the keystone service runs.
                          Defaults to "localhost".
* `keystone_admin_port`:  Keystone admin service port. Defaults to "35357".
* `admin_token`:          Keystone admin token

* `rabbit_hostname`:      hostname/IP address where the RabbitMQ service runs.
                          Defaults to "localhost".
* `rabbit_username`:      RabbitMQ username for glance.
                          It must already exist.
                          Defaults to "rabbit\_username\_default".
* `rabbit_pass`:          RabbitMQ password for glance.
                          Defaults to "rabbit\_pass\_default".

* `mysql_hostname`:       MySQL server address. Defaults to "localhost".
* `mysql_admin_username`: MySQL admin username. Defaults to "root".
* `mysql_rootpass`:       MySQL admin password. Defaults to "mysql\_root\_default".

# Role specific
* `glance_hostname`:      Hostname/IP address where this role runs.
                          It will be used to set keystone endpoints.
                          Defaults to the first interface IP address (i.e., eth0).

* `glance_port`:          Desired glance service port. Defaults to "9292".

* `glance_dbpass`:        Desired glance user password for the glance database.
                          Defaults to "glance\_dbpass\_default".

* `glance_pass`:          Desired password for the image service.
                          Defaults to glance\_pass\_default.

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: glance001
      roles:
        - role: openstack-glance
          mysql_rootpass: "{{ MYSQL_ROOT }}"
          rabbit_username: "openstack-glance"
          rabbit_pass: "{{ RABBIT_GLANCE_PASS }}"
          glance_dbpass: "{{ GLANCE_DBPASS }}"
          glance_pass: "{{ GLANCE_PASS }}"
          admin_token: "{{ ADMIN_TOKEN }}"

License
-------

Apache

Author Information
------------------

Davide Guerri - davide.guerri@gmail.com
