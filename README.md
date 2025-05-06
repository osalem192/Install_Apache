# Install Apache Role for Ansible

An Ansible role for automating the installation and basic configuration of the Apache HTTP Server (httpd) on RedHat Linux systems.

## 📆 Overview

This role simplifies the deployment of Apache by managing installation, service configuration, and default settings. It is designed to be modular and easily integrated into broader infrastructure automation workflows.

## 📁 Role Structure

The role follows the standard Ansible role directory structure:

```
Install_Apache/
├── defaults/
│   └── main.yml
├── files/
|   └── index.html
├── handlers/
│   └── main.yml
├── meta/
│   └── main.yml
├── tasks/
│   └── main.yml
├── tests/
│   └── test.yml
├── vars/
│   └── main.yml
└── .travis.yml
```


## 🔧 Role Variables

The role includes variables defined in `vars/main.yml`. You can override these variables as needed:

```yaml
# var/main.yml
pkg: httpd  # Apache name in redhat
svc: httpd  # Apache Service name in RedHat
port: 88 # Apache listen port
```

## How to use this role
1. **you need to create:**

    - ansible playbook
    - inventory
    - ansible config file

2. **you need to add role path in the ansible.cfg file**
3. **you need to add role path in your playbook file**

### example on inventory

``` yaml
[ws]
workstation

[webservers]
servera
serverb

[dbservers]
serverc
serverd

[nti:children]
webservers
dbservers
```

### example for ansible.cfg file

``` yaml
[defaults]
inventory = ~/inventory
remote_user = root
roles_path = /home/student/roles:/usr/share/ansible/roles:/etc/ansible/roles
```

## Example Playbook

Here's how to use the role in a playbook:

```yaml
- name: Install and configure Apache
  hosts: webservers
  become: yes
  roles:
    - Install_Apache
```

## How to run the PlayBook
you should run the following command in the playbook directory:

if you are using the navigator version
``` bash
anssible-navigator run -m stdout playbook_apache.yml
```

or if you are running ansible core version

```bash
anssible-playbook run -m stdout playbook_apache.yml
```

## 👤 Author

This was originally Authored by **Ahmed Orabi** but Modified and Maintained by **Omar Salem**. Feel free to contribute or raise issues for improvements.
