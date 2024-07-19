## What is Ansible?

Ansible is a configuration management and automation tool that simplifies the management of systems and applications. It automates software provisioning, configuration management, and application deployment.

## Types of Configuration Management Tools

There are several configuration management tools available, each with its own approach and strengths:

#### Ansible
- Uses SSH to communicate with servers and run tasks.
- YAML-based syntax for defining automation tasks.
- Known for simplicity, ease of use, and scalability.

#### Chef
- Uses a master-agent architecture with a Chef server (master) and Chef clients (agents).
- Recipes (Ruby-based) define tasks, and Cookbooks organize recipes.
- Supports both push and pull models for configuration management.

#### Puppet
- Uses a master-agent architecture with a Puppet master (server) and Puppet agents (nodes).
- Puppet DSL (Domain-Specific Language) defines configuration states.
- Focuses on enforcing desired system configurations and managing infrastructure as code.

## Ansible workflow

![Ansible Workflow - Tech World with Murali - Moole Muralidhara Reddy.png](https://github.com/techworldwithmurali/devops-zero-to-hero/blob/main/Day-20/images/Day%20%2020-Ansible%20Workflow%20-%20Moole%20Muralidhara%20Reddy%20-%20Tech%20World%20with%20Murali.png)


1. **Ansible Management Node:**
   - This is the central control node where Ansible is installed.
   - From this node, you define and run your automation tasks.

2. **Playbook:**
   - Playbooks are Ansible’s configuration, deployment, and orchestration language.
   - They are written in YAML and define the tasks to be executed on managed nodes.
   - Playbooks allow for the execution of multiple tasks in a specific order.

3. **Inventory:**
   - The inventory file lists all the managed nodes (hosts) and groups.
   - This file specifies which machines are being managed by Ansible and how to connect to them.
   - The default location for the inventory file is `/etc/ansible/hosts`.
   - In the diagram, the inventory contains groups like `[Group A]`, `[Group B]`, and hosts like `Host1`, `Host2`, etc.

4. **SSH Communication:**
   - Ansible uses SSH (Secure Shell) to communicate with the managed nodes.
   - This allows for secure command execution on remote servers without the need for additional software on the managed nodes.

5. **Managed Nodes:**
   - These are the servers that Ansible manages.
   - In the diagram, there are different groups of hosts like `Host 1 Group A`, `Host 2 Group B`, and `Host N Group N`.

### Workflow Explanation:

- The **Ansible Management Node** initiates the automation process by executing **playbooks**.
- The **inventory file** defines which servers will be managed and their grouping.
- The management node connects to the managed nodes using **SSH**.
- Tasks defined in the playbooks are executed on the managed nodes as per the defined inventory and roles.

----
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

----
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

There are two ways to set up SSH:
1. Manually
2. Using `ssh-copy-id`
----
### Setting Up the SSH Connection Manually

1. **Create the SSH key using the `ssh-keygen` command:**
   ```sh
   ssh-keygen
   ```
   Follow the prompts to save the key in the default location (`/home/your_username/.ssh/id_rsa`).

2. **Copy the `id_rsa.pub` key to the destination server's `authorized_keys` file:**
```sh
  cat  ~/.ssh/id_rsa.pub
```

3. **Connect to the destination server from the source server:**
   ```sh
   ssh user_name@server_ip_address
   ```
   You should now be able to log in to the destination server from the source server without entering a password.
----
### Setting Up the SSH Connection Using `ssh-copy-id`

1. **Create the SSH key using the `ssh-keygen` command:**
   ```sh
   ssh-keygen
   ```
   Follow the prompts to save the key in the default location (`/home/your_username/.ssh/id_rsa`).

2. **Copy the `id_rsa.pub` key to the destination server using the `ssh-copy-id` command:**
   ```sh
   ssh-copy-id user_name@server_ip_address
   ```
   Replace `user_name` with your username and `server_ip_address` with the destination server's IP address.

3. **Connect to the destination server from the source server:**
   ```sh
   ssh user_name@server_ip_address
   ```
   You should now be able to log in to the destination server from the source server without entering a password.
   
----
# Ansible Modules 

- Ansible modules are fundamental units of work in Ansible, responsible for executing tasks on remote systems managed by Ansible.
- These modules are designed to perform specific actions like installing packages, managing files, or interacting with cloud resources. Here's an overview of Ansible modules:


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

### Top Ansible Modules

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
