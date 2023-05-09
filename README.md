stuttgart-things/configure-rke-node
====================================

prepares machines for rancher-ha deployment or as base installation for a downstream cluster node (w/ option for cloud-init). ([Rancher OS Requirements](https://rancher.com/docs/rke/latest/en/os/#operating-system)).

## INSTALLATION
```
cat <<EOF > /tmp/requirements.yaml
roles:
- src: https://github.com/stuttgart-things/configure-rke-node.git
  scm: git
  version: rke2r2-1.26.0
- src: https://github.com/stuttgart-things/install-requirements.git
  scm: git
  version: 05092023
  
collections: 
- name: community.crypto 
  version: 2.13.0 
- name: community.general 
  version: 6.6.0 
- name: ansible.posix 
  version: 1.5.2 
- name: kubernetes.core
  version: 2.4.0
EOF

pip3 install netaddr
ansible-galaxy install -r /tmp/requirements.yaml -f
```


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
