# Writing Simple Playbooks for basic understanding

vim install_nginx_wget.yaml
```
---
 - name: This is a play to install wget and nginx packages on the web servers group
   hosts: web
   gather_facts: no
   become: yes
   tasks:
   - name: Installing nginx pkg
     yum: name=nginx state=present
     become: yes
   - name: Installing wget pkg
     yum: name=wget state=present
     become: yes
```

ansible-playbook install_nginx_wget.yaml
