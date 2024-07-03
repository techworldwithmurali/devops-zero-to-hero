# Ansible

## What is Ansible?

Ansible is a configuration management and automation tool that simplifies the management of systems and applications. It automates software provisioning, configuration management, and application deployment.

## Types of Configuration Management Tools

There are several configuration management tools available, each with its own approach and strengths:

- **Ansible**: Ansible is agentless, using SSH to connect and manage remote servers.
- **Chef**: Chef uses a declarative approach to infrastructure automation, focusing on defining system states.
- **Puppet**: Puppet uses a declarative language to describe system configuration, enforcing desired state on managed systems.

### Version

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
