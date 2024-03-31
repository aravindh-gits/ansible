# Ansible

## Introduction
Ansible is an open-source automation tool that simplifies cloud provisioning, configuration management, application deployment, intra-service orchestration, and many other IT needs.

## Ansible Commands
- **ansible**: Runs a single task on your nodes.
- **ansible-playbook**: Executes Ansible playbooks.
- **ansible-vault**: Manages encrypted data within Ansible.

**Example:**
```bash
ansible all -m ping
```

## Structure of Ansible
Ansible uses playbooks, which are YAML files containing the desired state of your systems.

**Example:**
```yaml
- hosts: servers
  roles:
    - role: nginx
      vars:
        nginx_port: 80
```

## Variables and Datatypes
Variables in Ansible manage differences between systems and include strings, lists, and dictionaries.

**Example:**
```yaml
vars:
  http_port: 80
  max_clients: 200
```

## Ansible Vault
Ansible Vault is a feature that allows users to encrypt sensitive data within Ansible projects.

**Example:**
```bash
ansible-vault create credentials.yml
```

## Ansible Conditionals
Conditionals in Ansible are used to execute tasks based on certain conditions.

**Example:**
```yaml
tasks:
  - name: "Restart webserver"
    service:
      name: nginx
      state: restarted
    when: nginx_is_installed.rc == 0
```

## Ansible Roles and Tasks
Roles in Ansible allow the creation of reusable content, making it easier to deploy applications and manage systems.

**Example:**
```yaml
roles:
  - common
  - webserver
```

## Jinja2 Templates in Ansible
Jinja2 templates in Ansible are used to populate variables in files.

**Example:**
```jinja
My hostname is {{ ansible_hostname }}
```

## Active-Passive Deployment Strategy with Ansible
This strategy involves having a primary (active) system and a secondary (passive) system.

**Example:**
```yaml
- hosts: active_server
  tasks:
    - name: Ensure the service is running
      service:
        name: myservice
        state: started
```

## Ansible Error Handling
Ansible provides ways to handle errors during playbook execution.

**Example:**
```yaml
tasks:
  - name: This task might fail
    command: /bin/false
    ignore_errors: yes
```
