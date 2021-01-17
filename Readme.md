1. Introduction
    1. Before Ansible or Any other configuration Management tools
1. Ansible Architecture
1. Installing and Configuring Ansible
    1. Ansible Installation and Configuration
    1. Ansible Directory Structures
    1. How to disable host key checking?
    1. Inventory file with Groups and Group of Groups
    1. Different locations of ansible.cfg file with priority
    1. Review on Ansible Architecture
    1. Installing Ansible Engine
1. Ansible Ad-hoc commands
    1. Introduction to Ad-hoc commands
    1. Basic syntax for Ansible Ad-hoc commands
    1. How Ansible Works?
    1. Executing Ad-hoc commands or Playbooks
    1. Transfer a file from Ansible Engine to Nodes using copy module
    1. Download a file from Ansible Managed Nodes to Ansible Engine
    1. Create or Delete a file or directory on Managed Nodes
    1. List of different modules to work with files
    1. Install a package like git, httpd, mysql, git on Linux Systems using yum module
    1. Command Module
1. Ansible Facts and Variables
    1. Introduction to Ansible Facts
    1. How to create and work with custom facts?
    1. Ansible Inventories
1. Introduction to Docker and Containerization
    1.
1. Static and Dynamic Inventories
    1. Inventory Types and Working with AWS EC2 Dynamic Inventory Script
    1. Simple Custom Dynamic Inventory Script creation
    1. How to work with Managed nodes if managed nodes are not installed with Python
    1. Working with managed nodes using raw module
1. Password Authentication setup and explanation
    1. Working with Managed Nodes using a Password
    1. Password Authentication
    1. Executing Ansible tasks with default and different users on Managed Nodes
1. Ansible Variables
    1. Basic introduction to Ansible variables
1. Ansible Playbooks
    1. Introduction to Playbooks with task and play concepts
    1. Writing Simple Playbooks for basic understanding
    1. Basic Key Points to run Ansible Playbooks
1. Basic concepts to write Playbooks
    1. Working with different variables
    1. Print any message
    1. Variable and data types
    1. Data Structures/ Data Collections
    1. simple playbook to understand the usage of register and set_fact
    1. How to read a variable and print using an ansible playbook ?
    1. How to read variables from a yaml/json file ?
    1. Working with command line arguments
    1. Working with Gather facts variables or setup module variables
    1. working with inventory_hostname and hostvars variables
    1.
1. Using Helm to Automate Microservices Deployment on Kubernetes
    1. Understanding Helm Basics and Setting up Kubernetes Cluster
    1. Using Helm Charts to deploy Spring Boot Microservice to Kubernetes
    1. Using Helm Charts to manage Releases to Kubernetes Cluster
    1. Hands-On
1. Visual Studio Code Editor for Ansible Playbooks
    1. Installing and using Visual Studio Code Editor for Ansible Playbooks
    1. Operations on strings and numbers using Playbooks (Filters and Methods )
    1. Arithmetic operators on numbers
    1. simple practice on Arithmetic Operators
    1. Filters and Methods of Ansible Playbooks
1. Operators to work with tasks
    1. Comparison operators
    1. Membership operators and Test Operators
    1. Logical operators
1. Conditional Statements
    1. Settings for Ubuntu server to consider it as a Managed Node
    1. How to use when in a conditional statement?
    1. Inline conditional statement
1. Introduction to handlers
1. Loops
1. Tags
1. Error Handling
    1. ignore_errors
    1. failed_whenblock
    1. rescue
    1. always
    1. Error Handling with block and rescue
1. Ansible reusable concepts with: import_tasks,include_tasks
    1. Reusable tasks with import and include
1. loacal_action vs delegate_to
    1. Usage of local_action and delegate_to
1. Tomcat Installation and Configuration using Playbook
    1. Java and Tomcat installation and configuration using template module
1.
1. Template module
    1. Introduction to template module with variables
    1. Template variables, conditional statements and loops
1. Jinja Templating
    1. Template architecture
    1. Creating template files
    1. Jinja2 template with Conditionals
    1. Jinja2 template with filters
    1. Examples
        1. Template a file onto a remote host
        1. Test that a file is valid before templating onto the remote host
        1. Backup a file if template needs to overwrite it
        1. Template multiple files with a loop
        1. Capture template module output
1. AWS Provisioning Using Ansible
    1. Github link for playbooks
    1. Ansible Environment setup for AWS Provisioning
    1. Launch EC2 Instances with multiple security groups and Tags
    1. Simple playbooks to start stop and terminate ec2 instances
    1. Single playbook to start stop and terminate Instance
    1. EC2 Tags help to start, stop and terminate instances
    1. Cleanup Tag-less EC2 Instances using Playbooks
    1. Generate CSV Reports using ansible Playbooks for ec2 Instances
1. Ansible-Roles
    1. Converting a playbook into to Ansible Roles
1. Automating Helm using Ansible
    1. Ansible modules
    1. Access a Kubernetes cluster
    1. Install Python modules
    1. Start Kubernetes
    1. Get information about your cluster
    1. Use the k8s module
    1. Pull a container image with Podman
    1. Deploy with Ansible
    1. Examples
        1. Adding new Helm Repository
        1. Installing a Helm Chart
        1. Gather information about Helm Chart installed
        1. Install Helm Plugin
        1. Gather information about Helm plugins
