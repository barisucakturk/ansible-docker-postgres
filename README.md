Role Name
=========

Ansible role to manage and run the PostreSQL docker container. It optionally creates initial user and database.

It uses data container for persistence, which is more elegant way comparing to host volumes.


Requirements
------------

Ubuntu 14.04 is tested.

This role uses Ansible's docker module, so requirements are [the same](https://docs.ansible.com/ansible/docker_image_module.html#requirements-on-host-that-executes-module).

Role Variables
--------------

Here is the list of default variables with default values:

```
postgres_docker_image: postgres
postgres_docker_image_tag: 9.5
postgres_container_name: 'postgres'
postgres_port: 5432
```

Also you can set optional variables to create initial user/database.

```
postgres_user: db_user
postgres_password: db_password
postgres_database: my_db
```

Dependencies
------------

No dependencies

Example Playbook
----------------

    - hosts: database
      roles:
        - role: matic-insurance.docker-postgres
          tags: ['database]
          postgres_user: 'db_user'
          postgres_password: 'db_password' # better put to Vault
          postgres_database: 'my_db'

License
-------

MIT

Author Information
------------------

Matic is a communication platform that connects lenders and borrowers originating a new home loan. A borrower now knows where they are in the loan process and what they need to do to complete the loan.