update
=========
Upgrade system, update cache and set cache validity time to 86400s

Requirements
------------
None

Role Variables
--------------
None

Dependencies
------------
None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      vars:
        upgrade_type: safe
      gather_facts: true
      roles:
         - role: "update"

License
-------

BSD

