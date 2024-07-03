# Ansible

## What is Ansible?

Ansible is a configuration management and automation tool that simplifies the management of systems and applications. It automates software provisioning, configuration management, and application deployment.

## Types of Configuration Management Tools

There are several configuration management tools available, each with its own approach and strengths:

- **Ansible**: Ansible is agentless, using SSH to connect and manage remote servers.
- **Chef**: Chef uses a declarative approach to infrastructure automation, focusing on defining system states.
- **Puppet**: Puppet uses a declarative language to describe system configuration, enforcing desired state on managed systems.

# Installing Ansible on Linux

## Enable EPEL Repository

First, enable the EPEL repository which contains additional packages for Enterprise Linux:

```bash
yum install epel-release -y
```

## Install Ansible

Next, install Ansible using the following command:

```bash
yum install ansible -y
```

## Verify Installation

Check if Ansible has been installed successfully by running:

```bash
ansible --version
```

This command should display the installed version of Ansible.

## Configuration Files and Locations

Ansible uses several default files and directories for configuration and management:

- **Default Host (Inventory) File**: `/etc/ansible/hosts`
- **Default Ansible Config File**: `/etc/ansible/ansible.cfg`
- **Default Ansible Role Location**: `/etc/ansible/roles`
- **Changing Inventory File Location**: You can specify a different inventory file location in `/etc/ansible/ansible.cfg`.

## Default Repository Location

The default location for yum repositories on CentOS/RHEL systems is:

- `/etc/yum.repos.d`
---
# Ansible ad-hoc commands

Ansible ad-hoc commands are useful for performing quick tasks without the need for writing a playbook. Here are the three common ways to use Ansible ad-hoc commands:

1. **Using Module and Arguments**: This involves specifying both the Ansible module and its arguments to perform a specific task. For example:
   ```bash
   ansible localhost -m yum -a "name=httpd state=present"
   ```
   This command uses the `yum` module to ensure that the `httpd` package is installed (`state=present`).

2. **Using Module Only**: You can also use ad-hoc commands with just specifying the module, without additional arguments. For example:
   ```bash
   ansible localhost -m ping
   ```
   This command uses the `ping` module to check if the server is reachable and can respond.

3. **Using Arguments Only**: Sometimes, tasks can be executed using only Ansible arguments without specifying a module explicitly. For example:
   ```bash
   ansible localhost -a "yum install httpd -y"
   ```
   Here, Ansible runs the command `yum install httpd -y` directly on the localhost without specifying a module.

Regarding your examples:

- **Installing `httpd` package using module and arguments**:
  ```bash
  ansible localhost -m yum -a "name=httpd state=present"
  ```
  This ensures that the `httpd` package is installed using the `yum` module.

- **Installing `httpd` package using arguments only**:
  ```bash
  ansible localhost -a "yum install httpd -y"
  ```
  This command directly runs the `yum install httpd -y` command on the localhost.

- **Checking server status using the `ping` module**:
  ```bash
  ansible localhost -m ping
  ```
  This command checks if the server (localhost in this case) is reachable.

- **Copying the `murali` file to `/opt` directory using module and arguments**:
  ```bash
  ansible localhost -m copy -a "src=murali dest=/opt"
  ```
  This command uses the `copy` module to copy the `murali` file to the `/opt` directory on localhost.

- **Checking server setup using the `setup` module**:
  ```bash
  ansible localhost -m setup
  ```
  This command gathers facts about the server (localhost) using the `setup` module.

These examples illustrate how you can perform various tasks using Ansible ad-hoc commands, either by specifying a module and its arguments, using a module alone, or providing arguments directly for execution.
