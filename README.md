# What is ansible role 

An Ansible role is a reusable and self-contained unit of automation that encapsulates tasks, variables, files, and handlers necessary to accomplish a specific configuration or set of tasks on remote systems. Roles provide a structured way to organize and manage complex automation workflows in Ansible.

### Ansible Role Structure

When you create an Ansible role using `ansible-galaxy init rolename`, it sets up a directory structure with the following standard directories:

1. **defaults**: Contains default variables for the role. Variables defined here have the lowest priority and are easily overridden.
   
2. **vars**: Contains other variables for the role. Variables here have a higher priority than those in the `defaults` directory.

3. **handlers**: Contains handlers, which are used to trigger actions in response to events. Handlers are typically associated with services and can be notified by tasks.

4. **meta**: Contains metadata for the role, including information about the role itself (e.g., author, supported platforms) and any dependencies it may have.

5. **tasks**: Contains the main list of tasks to be executed by the role. This directory usually includes one or more YAML files defining tasks to configure the system.

6. **files**: Contains static files that need to be copied to the remote system as-is during playbook execution. The path to these files must be explicitly specified.

7. **templates**: Contains templates that use the Jinja2 templating engine. Templates allow for dynamic generation of configuration files based on variables and conditions.

### Example: Installing HTTPD Using an Ansible Role

Here's an example of how you might configure an Ansible role to install the Apache HTTP Server (`httpd`) on target hosts:

1. **Create the Role Structure**:

   ```bash
   ansible-galaxy init httpd
   ```

   This command creates a directory structure (`httpd/`) with the directories mentioned above.

2. **Edit the Role Tasks (`tasks/main.yml`)**:

   Inside `tasks/main.yml`, define the tasks to install `httpd`:

   ```yaml
   ---
   - name: Install Apache HTTPD
     yum:
       name: httpd
       state: present
     become: yes
   ```

   This task uses the `yum` module to install `httpd` on CentOS/RHEL systems. Adjust accordingly for other package managers (`apt`, `dnf`, etc.) and distributions.

3. **Use the Role in a Playbook**:

   Create a playbook (`install_httpd.yml`) that uses your `httpd` role:

   ```yaml
   ---
   - name: Install Apache HTTPD
     hosts: your_target_hosts
     become: yes
     roles:
       - httpd
   ```

   Replace `your_target_hosts` with the appropriate hosts or groups from your Ansible inventory.

4. **Run the Playbook**:

   Execute the playbook to install `httpd` on the specified hosts:

   ```bash
   ansible-playbook install_httpd.yml
   ```

   Ansible will apply the tasks defined in your role (`httpd/tasks/main.yml`) to the target hosts, installing `httpd` and handling any necessary configuration.

### Summary

Ansible roles provide a structured and reusable way to organize tasks, variables, files, and handlers for automating complex configurations and tasks across multiple systems. They help maintain consistency, simplify maintenance, and promote best practices in Ansible playbook development.

----

### What is Ansible Vault?

Ansible Vault helps secure sensitive information within Ansible projects by encrypting data files, variables, and even entire playbooks. It uses AES (Advanced Encryption Standard) encryption to keep data secure.

### Ansible Vault Commands

Here are the key commands used with Ansible Vault:

1. **Create a New Encrypted File:**

   ```bash
   ansible-vault create filename
   ```

   This command creates a new file (`filename`) and prompts you to enter and confirm a vault password. This password is used to encrypt the file.

2. **Encrypt an Existing File:**

   ```bash
   ansible-vault encrypt filename
   ```

   Encrypts an existing plaintext file (`filename`). If the file already contains encrypted data, it will re-encrypt it with a new password.

3. **Decrypt a Vault File:**

   ```bash
   ansible-vault decrypt filename
   ```

   Decrypts an encrypted file (`filename`). You must provide the vault password to decrypt the file.

4. **Edit an Encrypted File:**

   ```bash
   ansible-vault edit filename
   ```

   Opens an encrypted file (`filename`) for editing. You need to provide the vault password. Ansible will decrypt the file, allow you to make changes, and then re-encrypt it after saving.

5. **View an Encrypted File:**

   ```bash
   ansible-vault view filename
   ```

   Opens an encrypted file (`filename`) for viewing. Similar to `edit`, but you cannot make changes. You must provide the vault password.

6. **Rekey a Vault File:**

   ```bash
   ansible-vault rekey filename
   ```

   Changes the password used to encrypt an already encrypted file (`filename`). You need to provide the old password and then set a new one.

### Using Ansible Playbooks with Vault

When running playbooks that contain encrypted files:

- **Running with `--ask-vault-pass`:**

  ```bash
  ansible-playbook filename.yml --ask-vault-pass
  ```

  Prompts you to enter the vault password during playbook execution.

- **Running with `--vault-password-file`:**

  ```bash
  ansible-playbook filename.yml --vault-password-file=path/to/password_file
  ```

  Specifies a file containing the vault password, allowing for automated execution without manual input.

### Best Practices

- **Managing Passwords:** Store your vault passwords securely. Avoid hardcoding passwords directly in playbooks or using version control for password files.

- **Rotation:** Periodically change vault passwords for added security.

- **Scope:** Encrypt only sensitive data that needs protection, such as passwords, API keys, or other confidential information.

Ansible Vault is crucial for managing sensitive information securely within Ansible projects, ensuring that sensitive data is protected both at rest and in transit during playbook execution.
