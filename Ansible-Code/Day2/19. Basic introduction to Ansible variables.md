# Basic introduction to Ansible variables
 - Used to store values
 - Types of variables
   - Default Variables
   - Inventory Vars
     - For hosts and groups
   - Facts and Local Facts
   - Registed variables
 - Default Variables
   - Ansible defines some variables for us. These variables are very helpful. Below are few variables that Ansible defines for us:
     - inventory_hostname
     - inventory_hostname_short
     - groups
     - groups.keys()
 - Debug Module
   - For debugging purpose and just to display some information
   - Example:
     - ansible all -m debug -a "msg='This is debug module'"
   - It executes on the localhost only
   - It's used to display some information based on the requirement
   - To display variable value
   - Runs only on ansible engine
   - Commands
     - ansible all -m debug -a "var=inventory_hostname"
     - ansible all -m debug -a "msg={{inventory_hostname}}"
     - ansible all -m debug -a "var=inventory_hostname_short"
     - ansible localhost -m debug -a "var=groups"
     - ansible localhost -m debug -a "var=groups.keys()"
   - Host / Group Variables
     - We can specify host variables in inventory file
     - Below is the sample inventory file
     - ```
       [passwordless]
       3.86.167.167
       [password]
       45.23.4.56 ansible_ssh_user=user1 ansible_ssh_pass=user1@123
       ```
   - Create Group wise variables
     - We can specify group variables also to specify values for the specifiec group
     - Below is the sample inventory file
     ```
       [passwordless]
       3.86.167.167
       [password]
       45.23.4.56
       [password:vars]
       ansible_ssh_user=user1
       ansible_ssh_pass=user1@123
       [all:vars]
       ansible_ssh_user=ansadmin
       ansible_ssh_pass=ansadmin@123
       ```
     - Run below command now
       - ansible all -m file -a "path=atin.txt state=touch"
   - Priority (Highest to lowest)
     - host variables
     - specific group variables
     - all group variables     - 

    
