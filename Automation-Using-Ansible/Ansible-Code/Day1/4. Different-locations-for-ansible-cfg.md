# Different Locations of ansible.cfg

 - Based on priority (Highest to least)
   - ANSIBLE_CONFIG environment variable
     - export ANSIBLE_CONFIG=\<Any location of ansible.cfg\>
   - Current folder
     - ./ansible.cfg
   - User's home directory
     - ~/.ansible.cfg   (Note that it's .ansible.cfg)
   - Default ansible.cfg
     - /etc/ansible/ansible.cfg
 - ansible --version
 - 
 - cd
 - touch .ansible.cfg
 - ansible --version
 - 
 - cd ~/my_ansible_nprod
 - ansible --version
 - 
