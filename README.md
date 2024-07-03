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
- name: Install and configure Apache web server
  hosts: web_servers
  become: yes  # Run tasks with sudo privileges

  tasks:
    - name: Install Apache package
      package:
        name: apache2
        state: present

    - name: Ensure Apache service is started and enabled
      service:
        name: apache2
        state: started
        enabled: yes

    - name: Copy configuration file
      copy:
        src: /path/to/apache.conf
        dest: /etc/apache2/apache.conf
        owner: root
        group: root
        mode: 0644

    - name: Reload Apache service if config changed
      service:
        name: apache2
        state: reloaded
      notify:
        - Restart Apache

  handlers:
    - name: Restart Apache
      service:
        name: apache2
        state: restarted
```

### How Playbooks Work

1. **Execution Flow**: Ansible playbooks are executed sequentially from top to bottom, performing tasks defined under each play and handling dependencies between tasks.

2. **Idempotency**: Playbooks are designed to be idempotent, meaning they can be run multiple times without changing the system state once the desired state is achieved. This ensures consistency and reliability in automated tasks.

3. **Reporting and Output**: Ansible provides detailed output during playbook execution, showing the status of each task, any changes made, and potential errors encountered. This helps in debugging and monitoring automation tasks.

4. **Integration with Inventories**: Playbooks operate on hosts defined in Ansible inventory files, allowing for dynamic scaling and management of infrastructure based on defined host groups and variables.

### Benefits of Ansible Playbooks

- **Automation**: Enables the automation of complex and repetitive tasks, reducing manual intervention and human error.
  
- **Consistency**: Ensures consistent configuration and management of servers and applications across different environments.
  
- **Scalability**: Scales easily to manage hundreds or thousands of servers simultaneously through defined playbooks and inventories.

- **Reusability**: Playbooks, tasks, and roles can be reused across different projects and environments, promoting efficiency and standardization in IT operations.

-----
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

This playbook serves as a basic example. You can extend it with more tasks, variables, error handling, or include it in a larger playbook for managing multiple servers or more complex configurations.
