# Executing Ansible tasks with default and different users on Managed Nodes
 - Create a new user in any of the managed user
   - useradd user1
   - passwd user1
   - 
 - In case we need to execute ansible tasks using a diffetent user
   - ansible ip_of_vm -i hostfile_name -m ping
     - It will work using default user
   - ansible ip_of_vm -i hostfile_name -m ping -u user1
     - It will work using user specified