# Controlling where tasks run: delegation and local actions
 - By default Ansible gathers facts and executes all tasks on the machines that match the hosts line of your playbook
  - We can delegate tasks to a different machine or group, delegate facts to specific machines or groups, or run an entire playbook locally
  - For example, when updating your webservers, you might need to remove them from a load-balanced pool temporarily. You cannot perform this task on the webservers themselves. By delegating the task to localhost, you keep all the tasks within the same play.

## Tasks that cannot be delegated
 - Some tasks always execute on the controller
 - These tasks, including include, add_host, and debug, cannot be delegated.

```
---
- hosts: webservers
  serial: 5

  tasks:
    - name: Take out of load balancer pool
      ansible.builtin.command: /usr/bin/take_out_of_pool {{ inventory_hostname }}
      delegate_to: 127.0.0.1

    - name: Actual steps would go here
      ansible.builtin.yum:
        name: acme-web-stack
        state: latest

    - name: Add back to load balancer pool
      ansible.builtin.command: /usr/bin/add_back_to_pool {{ inventory_hostname }}
      delegate_to: 127.0.0.1

```

 - The first and third tasks in this play run on 127.0.0.1, which is the machine running Ansible. There is also a shorthand syntax that you can use on a per-task basis: local_action.  - Here is the same playbook as above, but using the shorthand syntax for delegating to 127.0.0.1:

```

---
# ...

  tasks:
    - name: Take out of load balancer pool
      local_action: ansible.builtin.command /usr/bin/take_out_of_pool {{ inventory_hostname }}

# ...

    - name: Add back to load balancer pool
      local_action: ansible.builtin.command /usr/bin/add_back_to_pool {{ inventory_hostname }}

```
