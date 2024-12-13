
# Docker-for-DevOps


# This Repository is for Anisble & Configuration Management Practice 

This Repository is made to practice Anisble in and implement daily life scenarios of a Devops Engineer.

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

## Anisble Architecture
![Anisble_Configuration_Management](/home/ali-fareed/Ali/Devops/Ansible/Images/Anisble Architecture.jpg)

# Key Concepts of Anisble

- Inventory: The inventory file lists the target hosts on which Ansible will run tasks. It can be a static file or generated dynamically.
- Playbooks: Playbooks are YAML files that define a set of tasks and configurations to be executed on target hosts.
- Tasks: Tasks are the individual units of work in Ansible. They represent actions to be performed on target hosts.
- Modules: Ansible provides a wide range of modules for various tasks, such as package installation, file manipulation, service management, etc.
- Roles: Roles are reusable units of playbooks. They encapsulate related tasks, handlers, variables, and files into a directory structure.


![Key_Concepts_of_Anisble](/home/ali-fareed/Ali/Devops/Ansible/Images/Key Concepts of Anisble.png)

# Install Ansible

    1. sudo apt-add-repository ppa:ansible/ansible
    2. sudo apt update
    3. sudo apt install ansible

    Go to /etc/ansible/hosts file and wrtie the public IP Address of servers in a group
    1. server_number ansible_host=Public_IP_Address

    To run a command in remote server, this is check if the remote srevers are pingable
    1. ansible group_name_of_servers -m ping

# Ansible Adhoc commands
- ad hoc commands are great for tasks you repeat rarely.
- -a is used for adhoc commands

    1. ansible all -a "df -h" -u ubuntu
    2. ansible servers -a "uptime" -u buntu

# Ansible modules commands
- Ansible modules are units of code that can control system resources or execute system commands

    -m is used for modules
    1. ansible all -m ping -u ubuntu

# Ansible Playbooks
- Ansible modules are units of code that can control system resources or execute system commands

    1.  ansible-playbook -v playbook_name.yml

    name: Date playbook
    hosts: servers
    tasks:
        - name: this will show the
    date
        command: date












# Ansible-for-DevOps
