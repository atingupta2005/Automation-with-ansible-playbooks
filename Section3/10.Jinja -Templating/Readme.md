# Jinja2 Templating
 - Jinja2 templates are template files that store variables that can change from time to time.
 - When Playbooks are executed, these variables get replaced by actual values defined in Ansible Playbooks
 - This way, templating offers an efficient and flexible solution to create or alter configuration file with ease.

## Template architecture
 - A Jinja2 template file is a text file that contains variables that get evaluated and replaced by actual values upon runtime or code execution
 - In a Jinja2 template file, you will find the following tags:
    - {{ }}  :
      - These double curly braces are the widely used tags in a template file and they are used for embedding variables and ultimately printing their value during code execution
    - {%  %} :
      - These are mostly used for control statements such as loops and if-else statements.
    - {#  #} :
      - These denote comments that describe a task.

### Creating template files
 - Here’s an example of a Jinja2 template file example_template.j2 which we shall use to create a new file with the variables  shown
```
Hey guys!
Apache webserver {{ version_number }} is running on {{ server }}
Enjoy!
```
 - Here, the variables are {{ version_number }} & {{ server }


 - These variables are defined in a playbook and will be replaced by actual values in the playbook YAML file
 - When the playbook is executed, the variables in the template file get replaced by the actual values and a new file is created

### Jinja2 template with filters
 - Filters are used to alter the appearance of output or formatting data. This works by piping the variable name as shown:
```
{{ variable | argument }}
```

 - Examples:
```
{{ [ 100, 37, 45, 65, 60, 78 ] | min }}     =>   37
{{ [ 100, 37, 45, 65, 60, 78 ] | max }}     =>   100
{{ [ 3, 4, 3, 3, 4, 2, 2 ] | unique }}     =>   3,4,2
{{ ” Hello guys” | replace (“guys”, “world”) }} => Hello world
```

## Ansible template Module
 - Transfers templated files to remote hosts

### Special variables available inside templates
 - The following variables are available inside templates in addition to all available Ansible variables:
    - template_host
        - The node name of the host that executed the template (the local host).
    - template_path
        - The absolute path to the template on the local host.
    - template_run_date
        - The date the template was rendered.

### Examples:

 - How to template a file onto a remote host
    - Set the src parameter to a jinja2 template in your ./templates/ directory and dest to the location on the remote host.
```
- name: template file to remote host
  template:
    src: my_app.conf.j2
    dest: $HOME/my_app.conf
```

 - How to backup a file if template needs to overwrite it
    - By default, the template module will overwrite a file if it already exists on the remote host
    - Use the backup parameter if you want to backup the file before it is overwritten:
```
- name: template file to remote host with backup
  template:
    src: my_app.conf.j2
    dest: $HOME/my_app.conf
    backup: true
```

 - How to template multiple files with a loop
    - Use the loop keyword to template multiple files.

    - In the example below I’d like to create a .gitconfig for each user on the system. Here’s the template:


```
#templates/gitconfig.j2
[user]
  name = {{ user.name }}
  username = {{ user.username }}
  email = {{ user.username }}@example.com
[core]
  excludesfile = /home/{{ user.username }}/.gitignore
```

  - In the template we reference the user variable, which is going to come from each item in a loop
  - We can template this into each user’s home directory with the following task:

```
- name: create .gitconfig for each user
  template:
    src: .gitconfig.j2
    dest: "/home/{{ user.username }}/.gitconfig"
    owner: "{{ user.username }}"
    group: "{{ user.username }}"
    mode: 0644
  become: true
  loop:
    - name: John Smith
      username: jsmith
    - name: Jane Doe
      username: jdoe
  loop_control:
    loop_var: user

```
 - Notice that we’ve used the loop_control and loop_var directives to change the loop variable to user instead of item


 - How to capture template module output
    - Use the register keyword to capture the output of the template module.
```
- name: template file to remote host
  template:
    src: my_app.conf.j2
    dest: $HOME/my_app.conf
  register: template_output
- debug: var=template_output
```

    - The debug task above will output the following:

```
ok: [123.123.123.123] => {
    "template_output": {
        "changed": true,
        "checksum": "120ec4bdd3cea15350829527ecbdb59604fafa11",
        "dest": "/home/ubuntu/my_app.conf",
        "diff": [],
        "failed": false,
        "gid": 1000,
        "group": "ubuntu",
        "md5sum": "62ca3280a599503f968d8ba8fa2fefd8",
        "mode": "0664",
        "owner": "ubuntu",
        "size": 43,
        "src": "/home/ubuntu/.ansible/tmp/ansible-tmp-1545979819.76-238399833013342/source",
        "state": "file",
        "uid": 1000
    }
}
```
