Glance
=========

OpenStack Glance image service installation

_Tested on Ubuntu Precise (12.04) and Trusty (14.04)_

Requirements
------------

A MySQL server. See below.

A RabbitMQ server. See below.

A Keystone server. See below.

Role Variables
--------------


### Glance (set by this role)

| Name | Default value | Description | Note |
|---  |---  |---  |--- |
| `glance_dbpass` | `glance_dbpass_default` | Desired glance user password for the glance ||
| `glance_hostname` | `localhost` | Hostname/IP address where this role runs, it will be used to set keystone endpoints ||
| `glance_pass` | `glance_pass_default` | Desired password for the image service ||
| `glance_port` | `9292` | Desired glance service port ||
| `glance_protocol` | `http` | Desired glance protocol (http/https) | WiP, do not use. |


### Keystone (must exist)

| Name | Default value | Description | Note |
|---  |---  |---  |--- |
| `admin_token` | `admin_token_default` | Keystone admin service token ||
| `keystone_admin_port` | `35357` | Keystone admin service port ||
| `keystone_hostname` | `localhost` | Hostname/IP address where the keystone service runs ||
| `keystone_port` | `5000` | Keystone service port ||
| `keystone_protocol` | `http` | Desired glance protocol (http/https) | WiP, do not use. |


### MySQL (must exist)

| Name | Default value | Description | Note |
|---  |---  |---  |--- |
| `mysql_admin_username` | `root` | MySQL admin username ||
| `mysql_hostname` | `localhost` | MySQL server address ||
| `mysql_rootpass` | `mysql_root_default` | MySQL admin password ||


### RabbitMQ (must exist)

| Name | Default value | Description | Note |
|---  |---  |---  |--- |
| `rabbit_hostname` | `localhost` | Hostname/IP address where the RabbitMQ service runs ||
| `rabbit_username` | `rabbit_username_default` | RabbitMQ username for glance ||
| `rabbit_pass` | `rabbit_pass_default` | RabbitMQ password for glance. ||


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
          glance_hostname: "{{ ansible_eth0.ipv4.address }}"

License
-------

Apache

Author Information
------------------

Davide Guerri - davide.guerri@gmail.com
