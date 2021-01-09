# Types of Ansible Facts
  - Default facts
  - Custom facts
    - To get user defined facts
      - Example: Get the version of all the installed packages on managed nodes
  - Commands to collect facts using ad-hoc commands
    - ansible all -m ping
    - ansible all -m shell -a "git --version"
    - ansible all -m shell -a "/usr/sbin/httpd --version"
- Steps to create Custom facts
  - On Managed Nodes
    - sudo su
    - mkdir /etc/ansible/facts.d
    - cd /etc/ansible/facts.d
    - touch file1.fact
    - touch file2.fact
    - chmod 777 file1.fact
    - chmod 777 file2.fact
    - rm file1.fact
    - rm file2.fact
  - The output of fact file should a json
  
## Use Ansible to create /etc/ansible/facts.d automatically on all managed nodes
 - cd /etc/ansible
 - sudo mkdir facts.d
 - sudo su
 - cd facts.d
 - ls
 - yum install git
 - yum install httpd
 - pwd
 - git --version
 - httpd -version
 - git --version | awk '{print $3}'
 - httpd -version | awk 'NR==1 {print $3}'
 - touch git_httpd_version.fact
  ```
#!/bin/bash
git_ver=$(git --version | awk '{print $3}')
httpd_ver=$(/usr/sbin/httpd -version | awk 'NR==1 {print $3}')
cat << EOF
{
"Git_version": "$git_ver",
"httpd_version": "$httpd_ver"
}
EOF


  ```

 - chmod a+x git_httpd_version.fact

 - ./git_httpd_version.fact

 - sudo su ansadmin
 - cd ~/my_ansible_nprod
 - ls
 - ansible localhost -m setup | grep -i git_ver
 - ansible localhost -m setup -a "filter=ansible_local"

## Deploy custom facts on managed nodes
 - ansible all -m file -a "path=/etc/ansible/facts.d state=directory" -b
 - ansible all -m copy -a "src=/etc/ansible/facts.d/git_httpd_version.fact dest=/etc/ansible/facts.d/git_httpd_version.fact mode='0755'" -b
 - ansible all -m setup -a "filter=ansible_local"