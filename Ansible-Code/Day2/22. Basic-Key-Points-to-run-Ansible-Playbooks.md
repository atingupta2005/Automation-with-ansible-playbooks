# Basic Key Points to run Ansible Playbooks
- Use shebang
  - We can specify shebang string in the playbook
  - vim install_wget_nginx.yaml
```
#!/usr/bin/ansible-playbook
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
 - Run playbook having shebang string
   - chmod a+x ./install_wget_nginx.yaml
   - ./install_wget_nginx.yaml
- To check syntax
  - ansible-playbook install_wget_nginx.yaml --syntax-check
- To dry run
  - ansible-playbook install_wget_nginx.yaml --check
- To check verbose log
  - ansible-playbook install_wget_nginx.yaml -v
  - ansible-playbook install_wget_nginx.yaml -vvv
  - ansible-playbook install_wget_nginx.yaml -vvvvvv
