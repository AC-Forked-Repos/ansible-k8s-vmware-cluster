Role Name
=========

Role to mount NFS drive on distant server.

Requirements
------------

  Require nfs-common package on distant server.


Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

  Mandatories variables :
    nfs_server_ip: NFS server IP
    nfs_src_directory: Source directory on NFS server
    nfs_dest_directory: Destination directory on distant machine

  Predefined but overloadable
    nfs_opts: Define NFS mount options. Default value is "rw,sync,hard,intr,_netdev"


Dependencies
------------

None.


Example Playbook
----------------

    - hosts: servers
      roles:
        - role: "nfs-mount"
          vars:
            nfs_server_ip: 10.1.33.11
            nfs_src_directory: /export
            nfs_dest_directory: /mnt/network
        - role: "nfs-mount"
          vars:
            nfs_server_ip: 10.1.33.11
            nfs_opts: rw,sync,hard,intr,_netdev
            nfs_src_directory: /export
            nfs_dest_directory: /mnt/network


License
-------

BSD

Author Information
------------------
