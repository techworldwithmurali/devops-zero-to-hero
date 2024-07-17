### Working with `rm`

1. **Removing Files:**
   - To remove a file `filename` forcefully (`-f`):
     ```
     rm -f filename
     ```
   - The `-f` flag ensures that the file is deleted without prompting for confirmation.

2. **Removing Directories:**
   - To remove a directory `directory` recursively and forcefully (`-r` and `-f`):
     ```
     rm -rf directory
     ```
   - Use with caution as it deletes the directory and its contents recursively without confirmation.

### Creating and Deleting Users

1. **Creating Users:**
   - To create a user `user_name`:
     ```
     useradd user_name
     ```
     or
     ```
     adduser user_name
     ```

2. **Checking User Information:**
   - To check if a user exists and view their details:
     ```
     id user_name
     ```
     or
     ```
     cat /etc/passwd
     ```

3. **Deleting Users:**
   - To delete a user `user_name` and remove their home directory and mail spool (`-r`):
     ```
     userdel -r user_name
     ```

### Creating and Deleting Groups

1. **Creating Groups:**
   - To create a group `group_name`:
     ```
     groupadd group_name
     ```

2. **Checking Group Information:**
   - To view groups and their details:
     ```
     cat /etc/group
     ```

3. **Deleting Groups:**
   - To delete a group `group_name`:
     ```
     groupdel group_name
     ```

4. **Adding Users to Groups:**
   - To add `user_name` to an existing `group_name`:
     ```
     usermod -a -G group_name user_name
     ```

### Working with `head`

- The `head` command displays the first few lines of a file.
- To display the first 10 lines of `filename`:
  ```
  head filename
  ```
- To display the first `num` lines (e.g., 5 lines) of `filename`:
  ```
  head -n 5 filename
  ```

### Working with `tail`

- The `tail` command displays the last few lines of a file.
- To display the last 10 lines of `filename`:
  ```
  tail filename
  ```
- To display the last `num` lines (e.g., 5 lines) of `filename`:
  ```
  tail -n 5 filename
  ```

### Working with `top`

- The `top` command provides a dynamic view of processes running on the system.
- To view system summary and processes:
  ```
  top
  ```

### Working with `free`

- The `free` command displays memory usage information.
- To display memory usage in a human-readable format:
  ```
  free -h
  ```
## What is YUM
- YUM (Yellowdog Updater Modified) is an open source command-line as well as graphical based package management tool for RPM (RedHat Package Manager) based Linux systems. 
- It allows users and system administrator to easily install, update, remove or search software packages on a systems.
- If you want to keep your system up-to-date, you can enable automatic updates via yum-cron.
- By default yum is installed in server so you do not need to install it separately.
  
### YUM Commands and Examples

1. **Installing a Package:**
   - To install a package `packagename`:
     ```
     yum install packagename -y
     ```
   - The `-y` flag automatically answers yes to any prompts.

2. **Removing a Package:**
   - To remove a package `packagename`:
     ```
     yum remove packagename -y
     ```

3. **Updating a Package:**
   - To update a specific package `packagename`:
     ```
     yum update packagename
     ```

4. **Checking Available Package Updates:**
   - To check if there are updates available for installed packages:
     ```
     yum check-update
     ```

5. **Listing Installed Packages:**
   - To list installed packages matching `packagename`:
     ```
     yum list installed packagename
     ```

6. **Searching for Packages:**
   - To search for packages matching `packagename`:
     ```
     yum search packagename
     ```

7. **Getting Package Information:**
   - To view detailed information about `packagename`:
     ```
     yum info packagename
     ```

8. **Viewing YUM Command History:**
   - To view the history of YUM commands:
     ```
     yum history
     ```
----

### What is RPM
- RPM (Red Hat Package Manager) is an default open source and most popular package management utility for Red Hat based systems like (RHEL,  CentOS and Fedora). 
- The tool allows system administrators and users to  install,  update,  uninstall,  query, verify and manage system software packages in Unix/Linux operating systems. 
- The RPM formerly known as .rpm file, that includes compiled software programs and libraries needed by the packages. 
- This utility only works with packages that built on .rpm format.
- RPM doesn’t allow you to automatically update/upgrade packages installed on your system.
- It doesn’t resolve dependencies, you must install them manually.

### RPM Commands and Examples

1. **Installing a Package:**
   - To install a package `jfrog-artifactory-cpp-ce-7.6.2.rpm`:
     ```
     rpm -ivh jfrog-artifactory-cpp-ce-7.6.2.rpm
     ```
     - `-i`: Install the package.
     - `-v`: Verbose output.
     - `-h`: Show hash marks (#) indicating progress.

2. **Checking Installed RPM Packages:**
   - To check if a package `package_name` is installed:
     ```
     rpm -qa package_name
     ```
     - `-q`: Query mode.
     - `-a`: All packages installed.

3. **Updating a Package:**
   - To update a package `jfrog-artifactory-cpp-ce-7.6.2.rpm`:
     ```
     rpm -Uvh jfrog-artifactory-cpp-ce-7.6.2.rpm
     ```
     - `-U`: Upgrade mode.

4. **Removing a Package:**
   - To remove a package `package_name`:
     ```
     rpm -ev package_name
     ```
     - `-e`: Erase mode.

5. **Installing a RPM Package Without Dependencies:**
   - To install `jfrog-artifactory-cpp-ce-7.6.2.rpm` without checking dependencies:
     ```
     rpm -ivh --nodeps jfrog-artifactory-cpp-ce-7.6.2.rpm
     ```
     - `--nodeps`: Skip dependency checks.

6. **Checking Dependencies of RPM Package:**
   - To check dependencies of `jfrog-artifactory-cpp-ce-7.6.2.rpm` before installing:
     ```
     rpm -qpR jfrog-artifactory-cpp-ce-7.6.2.rpm
     ```
     - `-q`: Query mode.
     - `-p`: Specify the package file.
     - `-R`: List dependencies.
    
----
### What is find command
- find command is  used to find the files and directories and perform subsequent operations on them. 
- It supports searching by file, folder, name, creation date, modification date, owner and permissions.

### Working with `find` Command

1. **Finding Files by Name:**
   - To find `murali.txt` file in the current directory (`.`):
     ```
     find . -name murali.txt
     ```

2. **Finding Files Under a Specific Directory:**
   - To find files named `muni.txt` under `/opt` directory:
     ```
     find /opt -name muni.txt
     ```

3. **Finding Files Ignoring Case:**
   - To find files named `sunil.txt` under `/opt` directory ignoring case:
     ```
     find /opt -iname sunil.txt
     ```
     - `-iname`: Case-insensitive name search.

4. **Finding Directories:**
   - To find directories under `/opt` directory named `suresh`:
     ```
     find /opt -type d -iname suresh
     ```
     - `-type d`: Search only directories.

5. **Finding Files by Extension:**
   - To find all `.txt` files under `/opt` directory:
     ```
     find /opt -iname "*.txt"
     ```
     - `"*.txt"`: Matches all files ending with `.txt`.

6. **Finding Empty Files and Directories:**
   - To find all empty files under `/root` directory:
     ```
     find /root -type f -empty
     ```
     - `-type f`: Search only regular files.

   - To find all empty directories starting from root (`/`):
     ```
     find / -type d -empty
     ```
     - `-type d`: Search only directories.
    
----

### df (Disk Free)
- **Usage:** Checks disk space usage of file systems.
- **Examples:**
  - `df -h`: Displays disk space in human-readable format.
  - `df -a`: Displays all file systems, including those with 0 blocks.
----
### du (Disk Usage)
- **Usage:** Displays disk usage of files and directories.
- **Examples:**
  - `du -h`: Displays disk usage in human-readable format.
  - `du /root -h`: Checks disk usage of the `/root` directory.
----
### ps (Process Status)
- **Usage:** Displays information about processes running in the system.
- **Examples:**
  - `ps`: Displays processes running in the current shell.
  - `ps -A`: Displays all processes currently running.
  - `ps -T`: Displays processes associated with the current terminal.
  - `ps -u tomcat`: Displays processes associated with the user `tomcat`.
  - `ps -ef | grep 8080`: Checks if a process with port 8080 is running.
----
### kill
- **Usage:** Terminates processes.
- **Examples:**
  - `kill -9 PID`: Sends a SIGKILL signal to terminate a process by its PID.
  - `kill -3 PID`: Sends a SIGQUIT signal to a process for a thread dump.
----

### env
- **Usage:** Displays or modifies environment variables for the current shell session or executes a command in a modified environment.
- **Example:** 
  - `env`: Displays all environment variables.
  - `env VAR=value command`: Executes `command` with `VAR` set to `value` in its environment.
----
### export
- **Usage:** Sets an environment variable.
- **Example:** 
  - `export PATH=$PATH:/new/directory`: Adds `/new/directory` to the `PATH` environment variable.
  - `export VAR=value`: Sets `VAR` to `value` in the current shell environment.
----
### echo
- **Usage:** Prints text or variables to the terminal.
- **Example:** 
  - `echo "Hello, World!"`: Prints `Hello, World!` to the terminal.
  - `echo $HOME`: Prints the value of the `HOME` environment variable.
----
### tac
- **Usage:** Concatenates and prints files in reverse order line by line.
- **Example:** 
  - `tac file.txt`: Prints lines of `file.txt` in reverse order.
----
### sleep
- **Usage:** Delays for a specified amount of time.
- **Example:** 
  - `sleep 5`: Pauses execution for 5 seconds.
----
### exit
- **Usage:** Exits a shell or script.
- **Example:** 
  - `exit`: Exits the current shell session.
  - `exit 1`: Exits a script with a status code indicating an error (non-zero status).
----
### diff
- **Usage:** Compares files line by line and outputs the differences.
- **Example:** 
  - `diff file1.txt file2.txt`: Compares `file1.txt` and `file2.txt`, showing differences.
