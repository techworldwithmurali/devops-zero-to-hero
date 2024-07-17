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
You've provided a good overview of using YUM (Yellowdog Updater Modified) on RPM-based Linux systems. Here's a breakdown of the commands you mentioned with examples:

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
