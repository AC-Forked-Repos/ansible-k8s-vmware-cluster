# Ansible Roles and Playbooks

# Infrastructure configuration

## Inventory inventories/cloud-inventory.yaml
```yaml
all:
  children:
    ungrouped:
      hosts:
        admin-server:
    api_loadbalancers:
      hosts:
        k8s-api-lb-[01:02]:
    etcd_loadbalancers:
      hosts:
        k8s-etcd-lb-[01:02]:
    masters:
      hosts:
        k8s-master-[01:05]:
    etcds:
      hosts:
        k8s-etcd-[01:05]:
    workers:
      hosts:
        k8s-worker-[01:05]:
    nodes:
      children:
        etcds:
        masters:
        workers:
    loadbalancers:
      children:
        api_loadbalancers:
        etcd_loadbalancers:
    cluster:
      children:
        loadbalancers:
        nodes:
    servers:
      hosts:
        prometheus-server:
    nfs_servers:
      hosts:
        nfs-server-01:
        nfs-server-02:
    managed:
      children:
        nfs_servers:
        servers:
        cluster:
```
## Hosts /etc/hosts
### Administration server
```
10.1.55.11 admin-server.hawkfund.kr admin-server
```

### Monitoring Server
```
10.1.55.14 prometheus-server.hawkfund.kr prometheus-server
```

### NFS Server
```
10.1.55.201 nfs-server-01.hawkfund.kr nfs-server-01
10.1.55.202 nfs-server-02.hawkfund.kr nfs-server-02
```

### ETCD

#### ETCD load balancers VIP
```
10.1.55.40 k8s-etcd-lb-vip.hawkfund.kr k8s-etcd-lb-vip
```
#### ETCD load balancers
```
10.1.55.23 k8s-etcd-lb-01.hawkfund.kr k8s-etcd-lb-01
10.1.55.24 k8s-etcd-lb-02.hawkfund.kr k8s-etcd-lb-02
```

#### ETCD nodes
```
10.1.55.41 k8s-etcd-01.hawkfund.kr k8s-etcd-01
10.1.55.42 k8s-etcd-02.hawkfund.kr k8s-etcd-02
10.1.55.43 k8s-etcd-03.hawkfund.kr k8s-etcd-03
10.1.55.44 k8s-etcd-04.hawkfund.kr k8s-etcd-04
10.1.55.45 k8s-etcd-05.hawkfund.kr k8s-etcd-05
```

### Control plane

#### Control plane load balancers API and Ingress Controller load balancers VIP
```
10.1.55.20 k8s-api-lb-vip.hawkfund.kr k8s-api-lb-vip
```
#### Control plane API and Ingress Controller load balancers
```
10.1.55.21 k8s-api-lb-01.hawkfund.kr k8s-api-lb-01
10.1.55.22 k8s-api-lb-02.hawkfund.kr k8s-api-lb-02
```

#### Control plane
```
10.1.55.31 k8s-master-01.hawkfund.kr k8s-master-01
10.1.55.32 k8s-master-02.hawkfund.kr k8s-master-02
10.1.55.33 k8s-master-03.hawkfund.kr k8s-master-03
10.1.55.34 k8s-master-04.hawkfund.kr k8s-master-04
10.1.55.35 k8s-master-05.hawkfund.kr k8s-master-05
```

#### Workers 
```
10.1.55.51 k8s-worker-01.hawkfund.kr k8s-worker-01
10.1.55.52 k8s-worker-02.hawkfund.kr k8s-worker-02
10.1.55.53 k8s-worker-03.hawkfund.kr k8s-worker-03
10.1.55.54 k8s-worker-04.hawkfund.kr k8s-worker-04
10.1.55.55 k8s-worker-05.hawkfund.kr k8s-worker-05
```

## Playbooks

### Ansible
```
- ansible.yml
- user-ansible-copy-key.yml
- user-ansible-create.yml
- user-ansible-key-reload.yml
```

### System
```
- halt.yml
- reboot.yml
- set-hostname.yml
- set-hosts.yml
- update.yml
```

### Kubernetes

#### Kubernetes deployment on Rasberry Pi 4B
```
- k8s-RasberryPi-install.yml
```

#### Kubernetes deployment on VMware
```
- k8s-VMware-install.yml
```

#### Kubernetes remove
```
- k8s-nginx-remove.yml
- k8s-remove.yml
```

### NTP server
#### Chrony install
```
- chrony-server.yml
```

### NFS server
```
- set-nfs.yml
```

### Monitoring

#### Prometheus install
```
- prometheus.yml
```

#### Grafana install
```
- grafana.yml
```

### DevOps

#### Jenkins install
```
- jenkins.yml
```

- rasberry-get-temp.yml

# TODO
```
- terraform.yml
```

## Roles
### System roles
```
- system
- ntp  
```

### Rasberry Pi 4B roles
```
- rasberry  
```

### Docker roles
```
- docker
```

### Kubernetes roles
```
- k8s-RasberryPi  
- k8s-VMware  
```

### Load balancers
```
- haproxy  
- keepalived  
```

### Monitoring roles
```
prometheus  
grafana  
```

### DevOps
```
terraform
jenkins  
```


