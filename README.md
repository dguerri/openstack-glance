Glance
=========

OpenStack Glance image service installation

_Tested on Ubuntu Precise (12.04) and Trusty (14.04)_

Requirements
------------

A DBMS already configured with a user and a database (when applicable).

A RabbitMQ server. See below.

A Keystone server. See below.

Role Variables
--------------


### Glance (set by this role)

| Name | Default value | Description | Note |
|---  |---  |---  |--- |
| `glance_database_url` | `sqlite:////var/lib/glance/glance.sqlite` | Database URI ||
| `glance_hostname` | `localhost` | Hostname/IP address where this role runs, it will be used to set keystone endpoints ||
| `glance_pass` | `glance_pass_default` | Desired password for the image service ||
| `glance_port` | `9292` | Desired glance service port ||
| `glance_protocol` | `http` | Desired glance protocol (http/https) | WiP, do not use. |
| `keystone_admin_port` | `35357` | Keystone admin service port ||
| `keystone_hostname` | `localhost` | Hostname/IP address where the keystone service runs ||
| `keystone_port` | `5000` | Keystone service port ||
| `keystone_protocol` | `http` | Desired glance protocol (http/https) | WiP, do not use. |
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
          glance_database_url: "mysql://{{ MYSQL_GLANCE_USER }}:{{ MYSQL_GLANCE_PASS }}@{{ DATABASE_HOSTNAME }}/{{ MYSQL_GLANCE_DB }}"
          glance_hostname: glance
          glance_pass: "{{ GLANCE_PASS }}"
          keystone_hostname: keystone
          rabbit_hostname: rabbitmq
          rabbit_username: glance
          rabbit_pass: "{{ RABBIT_GLANCE_PASS }}"

---

A complete Ansible playbook demo, which uses this role, is available on Github (dguerri/vagrant-ansible-openstack) <https://github.com/dguerri/vagrant-ansible-openstack>

---


License
-------

Apache

Author Information
------------------

Davide Guerri - davide.guerri@gmail.com
