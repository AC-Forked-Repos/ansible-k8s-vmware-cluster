k8s-haproxy-install
=========
Install and configure Ha-Proxy load balancer for Kubernetes
Set fontend and backend for :
- Kubernetes Api kubectl
- http
- https
- ssh
Loop on Kubernetes Masters and Workers to fill server declaration lines.

Requirements
------------


Role Variables
--------------
These variables are set in hostvars but you can decrare it where you want.

haproxy_user_login: Set ansible user name
haproxy_user_password: Set ansible user password
kubernetes_loadbalancer_stats_port: Set port for Ha-Proxy statistic endpoint
kubernetes_loadbalancer_stats_endpoint: Set endpoint for Ha-Proxy statistics

These variables are set in group_vars but you can decrare it where you want.
kubernetes_loadbalanced_dns: Name of Ha-Proxy server
kubernetes_loadbalancer_ip: IP of Ha-Proxy server
kubernetes_loadbalancer_api_port: 6443 Kubernetes Api port
kubernetes_loadbalancer_http_port: 80 HTTP port for of Ha-Proxy server
kubernetes_loadbalancer_https_port: 443 HTTPS port for of Ha-Proxy server
kubernetes_loadbalancer_ssh_port: 22 SSH exposed port for frontend to joint administration server

kubernetes_admin_dns: Name of administration server
kubernetes_admin_ip: IP of administration server

Dependencies
------------
template/haproxy-rsyslog.j2
For log configuration

haproxy-configuration.j2
For frontend and backend declaration

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      become: yes
      gather_facts: true
      roles:
        - role: "k8s-haproxy-install"

License
-------

BSD
