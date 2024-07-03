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

----
# What is SSH

**SSH (Secure Shell)** is a network protocol that allows secure access to remote systems over an encrypted connection. It provides a secure channel over an unsecured network, such as the internet, allowing users to log into remote machines, execute commands, and transfer files securely.

In Ansible, SSH is the default method used for communication between the control node (where Ansible is installed and executed) and the managed nodes (where tasks are performed). Ansible uses SSH to connect to managed nodes, execute commands, and transfer files.

### Ways to Set Up SSH in Ansible

There are generally two main ways to set up SSH for use with Ansible:

1. **Password-Based Authentication**: This is the simpler method where Ansible connects to managed nodes using SSH with passwords. However, this method is less secure and less commonly used in production environments due to security concerns.

2. **Key-Based Authentication (Public Key Authentication)**: This is the recommended and more secure method for SSH authentication in Ansible. It involves generating SSH key pairs (public and private keys) on the control node and then copying the public key to the managed nodes. Ansible then uses the private key to authenticate SSH connections to the managed nodes.

### Setting Up SSH in Ansible

Here’s how you typically set up SSH for Ansible:

- **Generate SSH Key Pair**: On the control node (where Ansible is installed):
  ```bash
  ssh-keygen -t rsa
  ```
  Follow the prompts to generate a new SSH key pair.

- **Copy Public Key to Managed Nodes**: Use `ssh-copy-id` or manually copy the public key to each managed node:
  ```bash
  ssh-copy-id username@hostname
  ```
  Replace `username` and `hostname` with the appropriate values for your managed nodes.

- **Test SSH Connectivity**: Verify that Ansible can connect to managed nodes using SSH:
  ```bash
  ansible all -m ping
  ```
  This command uses the `ping` module to test connectivity to all managed nodes.

- **Configure Ansible Inventory**: Ensure your Ansible inventory (`hosts` file) contains the appropriate details (hostname, IP address, SSH port, etc.) for your managed nodes.
----
# Ansible Modules 

Ansible modules are fundamental units of work in Ansible, responsible for executing tasks on remote systems managed by Ansible. These modules are designed to perform specific actions like installing packages, managing files, or interacting with cloud resources. Here's an overview of Ansible modules:


### Types of Ansible Modules:

Ansible modules can be broadly categorized into several types based on their functionality:

1. **Core Modules**: These modules are included by default with Ansible and cover a wide range of system administration tasks. Examples include `file`, `copy`, `yum`, `apt`, `user`, `command`, `shell`, `service`, `ping`, etc.

2. **Community Modules**: These modules are contributed by the Ansible community and provide additional functionality beyond the core modules. They cover integrations with various platforms, services, and APIs. Examples include modules for AWS (`ec2`, `s3`, `iam`), Azure (`azure_rm`), Docker (`docker_container`, `docker_image`), Kubernetes (`k8s`, `k8s_scale`, `k8s_service`), etc.

3. **Custom Modules**: Users can create custom modules tailored to specific requirements using Python or any other programming language that can produce JSON output. Custom modules allow extending Ansible's capabilities to automate tasks unique to specific environments or applications.

### Using Modules in Ansible Playbooks:

Modules are invoked within Ansible playbooks to define tasks that need to be performed on managed nodes. Here’s an example of how a module (`yum`) is used in a playbook:

```yaml
---
- name: Ensure httpd is installed
  hosts: web_servers
  tasks:
    - name: Install httpd package
      yum:
        name: httpd
        state: present
```

In this playbook:
- `yum` is the module name.
- `name` and `state` are arguments passed to the module to specify the package (`httpd`) to be installed and its desired state (`present`).

### Advantages of Using Ansible Modules:

- **Simplicity**: Modules abstract complex tasks into simple, declarative statements within playbooks, making automation accessible even to those without extensive programming knowledge.
  
- **Consistency**: Idempotent behavior ensures that tasks are executed reliably and consistently, reducing errors and ensuring predictable outcomes across environments.

- **Extensibility**: With a vast library of core and community modules, Ansible can automate tasks across diverse systems, cloud platforms, and services, facilitating comprehensive infrastructure management.

The list you've provided ranks the top 100 Ansible modules based on their usage statistics as of January 2019. Here’s an overview of some of the most popular modules and their rankings:

### Top Ansible Modules (Based on Usage)

1. **file**: Used for managing files and directories on remote systems.
2. **include**: Includes and merges tasks from other files into the current playbook.
3. **template**: Manages file templates that utilize Jinja2 templating engine.
4. **command**: Executes shell commands on remote systems.
5. **service**: Manages services (start, stop, restart) on remote systems.
6. **shell**: Executes shell commands on remote systems, similar to `command` but with different handling.
7. **set_fact**: Sets Ansible facts or variables.
8. **apt**: Manages APT packages on Debian-based systems.
9. **lineinfile**: Ensures a particular line is in a file, or replaces an existing line.
10. **copy**: Copies files to remote locations.
11. **yum**: Manages YUM packages on Red Hat-based systems.
12. **assert**: Asserts the state of a system, useful for testing and validation.
13. **include_tasks**: Includes and executes a list of tasks from another file.
14. **stat**: Retrieves file or filesystem metadata.
15. **package**: A generic package manager module, useful for cross-platform package management.
16. **get_url**: Downloads files from HTTP, HTTPS, or FTP to a remote location.
17. **debug**: Prints statements during playbook execution, useful for debugging.
18. **import_tasks**: Imports and executes a list of tasks from another file.
19. **include_vars**: Loads variables from external YAML or JSON files.
20. **apt_repository**: Manages APT repositories on Debian-based systems.
