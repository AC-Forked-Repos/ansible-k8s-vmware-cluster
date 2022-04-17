common-packages
=========
Install minimum packages for ansible use
- net-tools
- telnet
- python3-pip
- sshpass
- nfs-common

and others packages for system administration
- tree

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
      become: yes
      gather_facts: true
      roles:
        - role: "common-packages"

License
-------

BSD