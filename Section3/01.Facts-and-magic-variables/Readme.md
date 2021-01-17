# Facts and magic variables
 - With Ansible you can discover certain variables containing information about your remote systems or about Ansible itself
 - Variables related to remote systems are called facts
 - With facts, you can use the behavior or state of one system as configuration on other systems.
 - For example, you can use the IP address of one system as a configuration value on another system
 - Variables related to Ansible are called magic variables.

## Ansible facts
 - Ansible facts are data related to your remote systems, including operating systems, IP addresses, attached filesystems, and more
 - You can access this data in the ansible_facts variable

```
- name: Print all available facts
  ansible.builtin.debug:
    var: ansible_facts

```

 - To see the ‘raw’ information as gathered, run this command at the command line:

```
ansible <hostname> -m ansible.builtin.setup

```

### Caching facts
 - Like registered variables, facts are stored in memory by default
 - However, unlike registered variables, facts can be gathered independently and cached for repeated use
 - With cached facts, you can refer to facts from one system when configuring a second system, even if Ansible executes the current play on the second system first
 - For example:

```
 {{ hostvars['asdf.example.com']['ansible_facts']['os_family'] }}
```

 - Caching is controlled by the cache plugins
 - By default, Ansible uses the memory cache plugin, which stores facts in memory for the duration of the current playbook run
 - To retain Ansible facts for repeated use, select a different cache plugin

## Information about Ansible: magic variables
 - You can access information about Ansible operations, including the python version being used, the hosts and groups in inventory, and the directories for playbooks and roles, using “magic” variables.
 - The most commonly used magic variables are:
    - hostvars,
      - Can access variables defined for any host in the play, at any point in a playbook
    - groups,
    - group_names, and
    - inventory_hostname

 - Other useful magic variables refer to the current play or playbook
  - ansible_play_batch
    - is a list of hostnames that are in scope for the current ‘batch’ of the play.
  - ansible_playbook_python
    - is the path to the python executable used to invoke the Ansible command line tool.

  - inventory_dir
    - is the pathname of the directory holding Ansible’s inventory host file.
  - inventory_file
    - is the pathname and the filename pointing to the Ansible’s inventory host file.
  - playbook_dir
      - contains the playbook base directory.
  - ansible_check_mode
      - is a boolean, set to True if you run Ansible with --check.
