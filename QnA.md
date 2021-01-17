# Questions and Answers

- How to set the default verbosity so that every time I run the playbook it will run with that verbosity level?
  - To set default verbosity, specify below settings in ansible.config
```
  verbosity   = 1
```
  - For more details, refer: https://acozine.github.io/html/reference_appendices/config.html

 - How to redirect Debug logs output to the log file instead of the screen?
    - In ansible.cfg, uncomment the below setting:
```
log_path = /var/log/ansible.log
```
