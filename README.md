# What is Ansible playbook

An Ansible playbook is a configuration management and orchestration tool that defines a set of instructions (tasks) for managing remote systems. It allows users to automate tasks such as software installation, configuration management, and application deployments across multiple servers or devices simultaneously. Here's an overview of Ansible playbooks:

### Key Concepts of Ansible Playbooks

1. **YAML Syntax**: Playbooks are written in YAML (YAML Ain't Markup Language), which is a human-readable data serialization standard. YAML syntax uses indentation to represent data structures and is easy to read and write.

2. **Tasks**: Playbooks consist of a series of tasks, each defined under a list of plays. Tasks can be simple, like installing a package, or complex, involving multiple steps such as configuring services or deploying applications.

3. **Plays**: A playbook can contain one or more plays. Each play defines a set of tasks to be executed on a specific group of hosts. Plays are defined with YAML dictionaries and include directives such as hosts, tasks, vars, and roles.

4. **Hosts**: Playbooks operate on groups of hosts defined in an Ansible inventory file. Hosts can be grouped based on different criteria like roles (web servers, database servers) or environments (development, production).

5. **Variables**: Ansible allows the use of variables within playbooks to parameterize tasks and make playbooks reusable across different environments. Variables can be defined globally, within plays, or even dynamically fetched from external sources.

6. **Handlers**: Handlers are special tasks triggered by other tasks within a playbook. They are used to manage services that need to be restarted or reloaded only once after a series of related tasks have been executed.

7. **Modules**: Playbooks utilize Ansible modules to perform specific actions on remote hosts. Modules are responsible for tasks like managing files, installing packages, starting services, and interacting with cloud services.

8. **Roles**: Roles are a way of organizing and structuring playbooks and tasks in a more modular and reusable manner. They encapsulate related tasks, variables, and files into directories that can be shared and reused across different playbooks.

### Example of an Ansible Playbook

Here's a simplified example of an Ansible playbook:

```yaml
---
- hosts: localhost
  tasks:
  - name: install httpd
    yum: name=httpd state=present
  - name: install git
    yum: name=git state=present

```
----
### How Playbooks Work

1. **Execution Flow**: Ansible playbooks are executed sequentially from top to bottom, performing tasks defined under each play and handling dependencies between tasks.

2. **Idempotency**: Playbooks are designed to be idempotent, meaning they can be run multiple times without changing the system state once the desired state is achieved. This ensures consistency and reliability in automated tasks.

3. **Reporting and Output**: Ansible provides detailed output during playbook execution, showing the status of each task, any changes made, and potential errors encountered. This helps in debugging and monitoring automation tasks.

4. **Integration with Inventories**: Playbooks operate on hosts defined in Ansible inventory files, allowing for dynamic scaling and management of infrastructure based on defined host groups and variables.
----
### Benefits of Ansible Playbooks

- **Automation**: Enables the automation of complex and repetitive tasks, reducing manual intervention and human error.
  
- **Consistency**: Ensures consistent configuration and management of servers and applications across different environments.
  
- **Scalability**: Scales easily to manage hundreds or thousands of servers simultaneously through defined playbooks and inventories.

- **Reusability**: Playbooks, tasks, and roles can be reused across different projects and environments, promoting efficiency and standardization in IT operations.

----
## How to install httpd and git using ansible playbook?

  Your Ansible playbook for installing `httpd` (Apache HTTP server) and `git` on localhost looks mostly correct. Here’s your playbook formatted properly:

```yaml
---
- hosts: localhost
  tasks:
    - name: Install httpd
      yum:
        name: httpd
        state: present

    - name: Install git
      yum:
        name: git
        state: present
```

### Explanation:

- **hosts**: Specifies the target hosts where the tasks will be executed. In this case, it's `localhost`, meaning the playbook will run on the machine where Ansible is executed.

- **tasks**: Defines a list of tasks to be performed. Each task includes:
  - **name**: A descriptive name for the task, which appears in the output when the playbook runs.
  - **yum**: The module used to manage packages via YUM (Yellowdog Updater Modified), a package manager for Red Hat-based systems like CentOS and Fedora.
    - **name**: Specifies the package name (`httpd` for Apache HTTP server and `git` for Git).
    - **state**: Specifies the desired state of the package (`present` ensures the package is installed).

### Running the Playbook:

To execute this playbook:

1. Save the playbook content to a file, for example, `playbook.yaml`.
2. Run the playbook using the `ansible-playbook` command:

   ```bash
   ansible-playbook playbook.yaml
   ```

3. Ansible will connect to `localhost`, install `httpd` and `git` if they are not already installed, and report back the status of each task.

### Notes:

- Make sure Ansible is installed on the machine where you run the playbook (`localhost` in this case).
- Ensure you have necessary permissions to install packages (`sudo` or root access if required).
- Verify the package names (`httpd` and `git`) are correct for your Linux distribution.

----
# ansible with_items
- The `with_items` directive in Ansible (also known as `loop` in newer versions of Ansible) is used to iterate over a list of items, allowing you to perform repetitive tasks more efficiently.
- It is commonly used in playbooks where you need to apply the same module (task) to multiple items, such as installing multiple packages, creating multiple users, or configuring multiple files.

Here’s how your playbook `with_items.yaml` works:

```yaml
---
- hosts: localhost
  tasks:
    - name: install softwares
      yum:
        name: "{{ item }}"
        state: present
      loop:
        - git
        - httpd
        - wget
```

### Explanation:

- **hosts**: Specifies the target hosts where the tasks will be executed. In this case, it's `localhost`, meaning the playbook will run on the machine where Ansible is executed.

- **tasks**: Defines a list of tasks to be performed. Each task includes:
  - **name**: A descriptive name for the task.
  - **yum**: The module used to manage packages via YUM (or another package manager).
    - **name**: Uses `{{ item }}` to dynamically insert each item from the `loop` directive.
    - **state**: Specifies `present` to ensure the package is installed (if not already).

- **loop**: Replaces the older `with_items` directive. It specifies a list of items to iterate over (`git`, `httpd`, `wget` in this case). Each iteration of the loop executes the task defined under `yum`, replacing `{{ item }}` with the current item in the list.

### Running the Playbook:

To execute this playbook:

1. Save the playbook content to a file, for example, `with_items.yaml`.
2. Run the playbook using the `ansible-playbook` command:

   ```bash
   ansible-playbook with_items.yaml
   ```

3. Ansible will connect to `localhost` and iterate over the list (`git`, `httpd`, `wget`), installing each package if it's not already installed.

### Notes:

- **Syntax**: Note the use of `{{ item }}` within the `yum` module, which is Ansible's way of referencing the current item in the loop.
- **Indentation**: YAML syntax relies on proper indentation to define structure and hierarchy. Ensure all tasks and directives are correctly indented.
- **Flexibility**: You can use `with_items` (or `loop`) with various modules beyond `yum`, such as `apt`, `file`, `copy`, etc., depending on the task you want to perform.

----

# Ansible Variables in Playbooks

Ansible variables allow you to assign values that can be reused throughout your playbook. They are useful for defining configurations, conditions, and more.

## Example: Using Variables in Playbooks

### `vars.yaml`

```yaml
---
- hosts: localhost
  vars:
    packages: "httpd, tree"
  tasks:
    - name: Install the software packages
      yum:
        name: "{{ packages }}"
        state: present
```

### Explanation

In this example:

- `packages`: This variable is defined to hold a string with package names separated by commas (`httpd, tree`).
- The `yum` module is used to install the packages specified in the `packages` variable on the `localhost`.
- `state: present` ensures that the packages are installed if they are not already installed.

### Usage

1. **Save the playbook**: Save the above YAML content in a file named `vars.yaml`.
2. **Run the playbook**: Execute the playbook using the `ansible-playbook` command:

   ```bash
   ansible-playbook vars.yaml
   ```

This will execute the playbook on the `localhost`, installing the specified packages (`httpd` and `tree` in this case).

----

# Using Tags in Ansible Playbook

Tags in Ansible allow you to selectively run or skip specific tasks within a playbook. This provides flexibility in playbook execution based on task categorization or requirements.

## Example: Using Tags in Playbook

### `tags.yaml`

```yaml
---
- hosts: localhost
  tasks:
    - name: Install httpd
      yum:
        name: httpd
        state: present
      tags:
        - httpd

    - name: Install wget
      yum:
        name: wget
        state: present
      tags:
        - wget
```

### Explanation

In this example:

- Two tasks (`Install httpd` and `Install wget`) are defined to install packages (`httpd` and `wget`) using the `yum` module on the `localhost`.
- Each task is assigned a tag (`httpd` for the first task and `wget` for the second task) using the `tags` keyword in Ansible.
- Tags allow you to categorize tasks based on their functionality or purpose.

### Running with Tags

#### Run Specific Tags

To execute tasks tagged with specific tags (`httpd` and `wget` in this case):

```bash
ansible-playbook tags.yaml --tags "httpd,wget"
```

This command runs only the tasks tagged with `httpd` and `wget`, skipping any tasks without these tags.

#### Skipping Specific Tags

To skip tasks tagged with specific tags (`java` and `git` for example):

```bash
ansible-playbook tags.yaml --skip-tags "java,git"
```

This command skips tasks tagged with `java` and `git`, executing all other tasks.

----

# Tomcat Installation Using Ansible Playbook

This Ansible playbook automates the installation of Apache Tomcat on remote hosts.

## Example Playbook: `tomcat.yml`

```yaml
---
- hosts: tomcat
  tasks:
    - name: Make sure that we can connect to the machine
      ping:

    - name: Add group "tomcat"
      group:
        name: tomcat

    - name: Add user "tomcat" and add to "tomcat" group
      user:
        name: tomcat
        group: tomcat
        createhome: yes
      become: true

    - name: Download Apache Tomcat
      get_url:
        url: https://archive.apache.org/dist/tomcat/tomcat-7/v7.0.106/bin/apache-tomcat-7.0.106.tar.gz
        dest: /opt/

    - name: Extract Tomcat archive
      unarchive:
        src: /opt/apache-tomcat-7.0.106.tar.gz
        dest: /opt/

    - name: Change ownership of Tomcat installation directory
      file:
        path: /opt/apache-tomcat-7.0.106/
        owner: tomcat
        group: tomcat
        state: directory
        recurse: yes

    - name: Copy Tomcat users configuration
      copy:
        src: tomcat-users.xml
        dest: /opt/apache-tomcat-7.0.106/conf/

    - name: Copy Tomcat systemd service file
      copy:
        src: tomcat.service
        dest: /etc/systemd/system/
        mode: 0755

    - name: Start Tomcat service
      service:
        name: tomcat
        state: started
        enabled: yes
```

**tomcat.service**

```xml
[Unit]
Description=Tomcat 9.0.87 service
After=network.target
[Service]
Type=forking
LimitNOFILE=65536
User=tomcat
Group=tomcat
ExecStart=/opt/tomcat/bin/startup.sh
ExecStop=/opt/tomcat/bin/shutdown.sh
Restart=Always
[Install]
WantedBy=multi-user.target
```
**tomcat-users.xml**
```xml
<?xml version='1.0' encoding='utf-8'?>
<tomcat-users xmlns="http://tomcat.apache.org/xml"
              xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
              xsi:schemaLocation="http://tomcat.apache.org/xml tomcat-users.xsd"
              version="1.0">

    <role rolename="manager-gui"/>
    <role rolename="manager-status"/>
    <role rolename="manager-script"/>
    <role rolename="manager-jmx"/>
    <role rolename="admin-gui"/>
    <role rolename="admin-script"/>

    <user username="tomcat" password="tomcat" roles="manager-gui,admin-gui,manager-status,manager-script,manager-jmx,admin-script"/>
</tomcat-users>
```


### Explanation

In this playbook (`tomcat.yml`):

- **Connection Check**: Ensures Ansible can connect to the target host (`ping` module).
- **Group and User Creation**: Creates a `tomcat` group and a `tomcat` user, adding the user to the group with a home directory (`user` module).
- **Download and Extract Tomcat**: Downloads Apache Tomcat from the specified URL (`get_url` module) and extracts it to `/opt/` (`unarchive` module).
- **Change Ownership**: Sets ownership of the Tomcat installation directory to `tomcat:tomcat` (`file` module).
- **Configuration Files**: Copies `tomcat-users.xml` to Tomcat's configuration directory (`copy` module).
- **Service Installation**: Installs Tomcat as a systemd service (`copy` module for `tomcat.service` and `service` module to start and enable the service).

### Usage

1. **Save the playbook**: Save the above YAML content in a file named `tomcat.yml`.
2. **Run the playbook**: Execute the playbook using the `ansible-playbook` command:

   ```bash
   ansible-playbook tomcat.yml
   ```

This playbook will automate the installation of Apache Tomcat on the specified `tomcat` hosts, performing all necessary setup steps including user and group creation, downloading Tomcat, configuring permissions, and starting the Tomcat service.
```
