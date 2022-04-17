rasberry-remove-swap
=========
Remove swapfile and disable swap for Kubernetes use on Rasberry Pi 4

Requirements
------------
Rasberry Pi 4

Role Variables
--------------
None

Dependencies
------------

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }
      vars:
        upgrade_type: safe
      become: yes
      gather_facts: true
      roles:
        - role: "rasberry-remove-swap"

License
-------

BSD