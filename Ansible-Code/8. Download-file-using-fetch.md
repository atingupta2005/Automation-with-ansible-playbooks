# Download a file using fetch module
 - First create a demo file in each managed node
   - touch /home/ansadmin/demo.txt 
   - echo "Hi" >> /home/ansadmin/demo.txt 
   - 

 - ansible all -m fetch -a "src=/home/ansadmin/demo.txt dest=./demo/"
 - tree ./demo/
 - If don't want to create directory structore by ip addresses
   - ansible all -m fetch -a "src=/home/ansadmin/demo.txt dest=./newdemo/{{inventory_hostname}}_demo.txt flat=yes"
 - Now inspect the content
   - tree ./newdemo/
   - cat ./newdemo/\<filename\>
 - 