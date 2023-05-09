stuttart-things/configure-rke-node
====================================

prepares machines for rancher-ha deployment or as base installation for a downstream cluster node (w/ option for cloud-init). ([Rancher OS Requirements](https://rancher.com/docs/rke/latest/en/os/#operating-system)).

Example play (RKE2)
-------------------

```
- hosts: all 
  become: true
  
  vars: 
    cloudinit: false 
    create_rke_user: false 
    update_os: true
    install_docker: false
    install_docker_compose: false 
    set_docker_proxy: false 
    template_creation_setup: false
    
  roles: 
    - role: configure-rke-node
```

License
-------




Author Information
------------------

Patrick Hermann
patrick.hermann@sva.de

Christian Mueller
christian.mueller@sva.de

04/2020
