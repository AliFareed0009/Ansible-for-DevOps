
# Ansible-for-DevOps


# This Repository is for Anisble & Configuration Management Practice 
- Introduction Ansible
- Architecture of Ansible
- Key Concepts
- Install Ansible
- Ansible adhoc Commands
- Ansible modules
- Ansible Playbooks

This Repository is made to practice Ansible in and implement daily life scenarios of a Devops Engineer.

## Folders

#### 

| Folder Name | Useages     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `Playbooks` | `nginx playbook` | A simple playbook to install, run and enable nginx in remote servers using ansible |


# The Following are topics covered in this Repository

## Introduction
- Ansible is an open-source automation tool used for configuration management,
application deployment, and orchestration.
- Ansible uses SSH for communication with target systems, making it agentless
and easy to set up.
 
## How Ansible works ?
- Ansible is agentless in nature, which means you don't need install any software on the manage nodes.
- For automating Linux and Windows, Ansible connects to managed nodes and pushes out small programs—called Ansible modules—to them. These programs are written to be resource models of the desired state of the system. Ansible then executes these modules (over SSH by default), and removes them when finished. These modules are designed to be idempotent when possible, so that they only make changes to a system when necessary.
- For automating network devices and other IT appliances where modules cannot be executed, Ansible runs on the control node. Since Ansible is agentless, it can still communicate with devices without requiring an application or service to be installed on the managed node.

## Anisble Architecture
![Anisble_Configuration_Management](https://github.com/AliFareed0009/Ansible-for-DevOps/blob/4c767fb21fe6c1e2f9c4768d7fbaec902f8d0884/Images/Anisble%20Architecture.jpg)

## How to setup Passwordless Authentication
- You need to set Passwordless Authentication in servers to run Ansible.

## Key Concepts of Anisble

- Inventory: The inventory file lists the target hosts on which Ansible will run tasks. It can be a static file or generated dynamically.
- Playbooks: Playbooks are YAML files that define a set of tasks and configurations to be executed on target hosts.
- Tasks: Tasks are the individual units of work in Ansible. They represent actions to be performed on target hosts.
- Modules: Ansible provides a wide range of modules for various tasks, such as package installation, file manipulation, service management, etc.
- Roles: An Ansible role is a reusable, self-contained unit of automation that is used to organize and manage tasks, variables, files, templates, and handlers in a structured way.

### Inventory
- Ansible inventory file is a fundamental component of Ansible that defines the hosts (remote systems) that you want to manage and the groups those hosts belong to. It provides Ansible with the information about the remote nodes to communicate with during its operations.

[webservers]
web1.example.com
web2.example.com

[dbservers]
db1.example.com
db2.example.com

[all:vars]
ansible_user=admin
ansible_ssh_private_key_file=/path/to/key

### Playbook
- A Playbook is a YAML file that defines a series of actions to be executed on managed nodes. It contains one or more "plays" that map groups of hosts to roles.


### Play
- A Play is a single, complete execution unit within a playbook. It specifies which hosts to target and what tasks to execute on those hosts. Plays are used to group related tasks and execute them in a specific order.

### Tasks
- Tasks are individual actions within a play that use modules to perform operations on managed nodes. Each task is executed in order and can include conditionals, loops, and handlers.

### Modules
- Modules are the building blocks of Ansible tasks. They are small programs that perform a specific action on a managed node, such as installing a package, copying a file, or managing services. Example


## Roles
- Tasks: The main list of actions that the role performs.
- Handlers: Tasks that are triggered by changes in other tasks, typically used for actions like restarting services.
- Files: Static files that need to be transferred to managed hosts.
- Templates: Jinja2 templates that can be rendered and transferred to managed hosts.
- Vars: Variables that are used within the role.
- Defaults: Default variables for the role, which can be overridden.
- Meta: Metadata about the role, including dependencies on other roles.
- Library: Custom modules or plugins used within the role.
- Module_defaults: Default module parameters for the role.
- Lookup_plugins: Custom lookup plugins for the role.

### Directory Structure of an Ansible Role

    An Ansible role follows a specific directory structure:

    <role_name>/
        ├── defaults/
        │   └── main.yml
        ├── files/
        ├── handlers/
        │   └── main.yml
        ├── meta/
        │   └── main.yml
        ├── tasks/
        │   └── main.yml
        ├── templates/
        ├── vars/
            └── main.yml

### Why Use Ansible Roles?
- Modularity: Roles allow you to break down complex playbooks into smaller, reusable components. Each role handles a specific part of the configuration or setup.
- Reusability: Once created, roles can be reused across different playbooks and projects. This saves time and effort in writing redundant code.
- Maintainability: By organizing related tasks into roles, it becomes easier to manage and maintain the code. Changes can be made in one place and applied consistently wherever the role is used.
- Readability: Roles make playbooks cleaner and easier to read by abstracting away the details into logically named roles.
- Collaboration: Roles facilitate collaboration among team members by allowing them to work on different parts of the infrastructure independently.

- Consistency: Using roles ensures that the same setup and configuration procedures are applied uniformly across multiple environments, reducing the risk of configuration drift.

![Key_Concepts_of_Anisble](https://github.com/AliFareed0009/Ansible-for-DevOps/blob/4c767fb21fe6c1e2f9c4768d7fbaec902f8d0884/Images/Key%20Concepts%20of%20Anisble.png)

# Install Ansible

    1. sudo apt-add-repository ppa:ansible/ansible
    2. sudo apt update
    3. sudo apt install ansible

    Go to /etc/ansible/hosts file and wrtie the public IP Address of servers in a group
    1. server_number ansible_host=Public_IP_Address

    OR

    Write the details of server in a group
    [group_name] e.g [web_servers]
    1. server_name ansible_host=Public_IP_Address

    To run a command in remote server, this is to check if the remote servers are pingable
    1. ansible group_name -m ping

# YAML
- YAML (YAML Ain't Markup Language) is a human-readable data serialization format that is commonly used for configuration files and data exchange between languages with different data structures.

# Syntax

    1. This is YAML Syntax
    
    Strings, Numbers and Booleans:
    string: Hello, World!
    number: 42
    boolean: true

    List
    fruits:
    - Apple
    - Orange
    - Banana

    Dictionary
    person:
        name: John Doe
        age: 30
        city: New York

    List of Dictionaries
    YAML allows nesting of lists and dictionaries to represent more complex data.

    family:
        parents:
            - name: Jane
            age: 50
            - name: John
            age: 52
        children:
            - name: Jimmy
            age: 22
            - name: Jenny
            age: 20


# Ansible Adhoc commands
- ad hoc commands are great for tasks you repeat rarely.
- -a is used for adhoc commands

# Syntax

    1. Adhoc Commands
    
    ansible all -a "df -h" -u ubuntu
    ansible servers -a "uptime" -u ubuntu