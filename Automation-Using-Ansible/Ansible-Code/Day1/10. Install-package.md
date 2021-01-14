# Install a package like git, httpt, mysql, ngixnx

 - ansible all -m yum -a "name=git state=present" -b
 - ansible all -m yum -a "name=httpd state=present" -b
 - Verify
   - which git
   - which httpd
   - 