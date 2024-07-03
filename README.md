### Linux Overview
Linux is a Unix-like operating system known for its stability, security, and open-source nature. It's widely used in servers, embedded systems, and desktop computers.

### Linux Distributions
Linux distributions (distros) package the Linux kernel with a collection of software to create complete operating systems. Examples include:

- **Amazon Linux:** Optimized for AWS EC2, integrates seamlessly with AWS services
- **Ubuntu**: User-friendly and widely used for desktop and server environments.
- **CentOS**: Popular for servers due to its stability and long-term support.
- **Debian**: Known for its stability and package management system.
- **Fedora**: Rapidly evolving with the latest features for developers.
- **Arch Linux**: Lightweight and customizable, favored by advanced users.

### Basic Commands

#### Navigation and File Management
- **pwd** (Print Working Directory):
  ```bash
  pwd
  ```
- **cd** (Change Directory):
  ```bash
  cd /path/to/directory
  ```
- **ls** (List Directory Contents):
  ```bash
  ls
  ls -l  # Detailed list
  ls -a  # Show hidden files
  ```
- **cal** (Display a Calendar):
  ```bash
  cal
  cal 2024  # Specific year
  ```
- **date** (Display Current Date and Time):
  ```bash
  date
  ```
- **history** (Display Command History):
  ```bash
  history
  ```
- **clear** (Clear the Terminal Screen):
  ```bash
  clear
  ```
- **man** (Manual Pages for Commands):
  ```bash
  man ls  # Get help for 'ls' command
  ```

#### System Information
- **Checking CPU and Memory Info**:
  ```bash
  cat /proc/cpuinfo
  cat /proc/meminfo
  ```
- **ping** (Check Network Connectivity):
  ```bash
  ping google.com
  ```
- **curl** (Transfer Data with URLs):
  ```bash
  curl https://example.com
  ```

#### User and System Information
- **who** and **whoami** (Display Current Users):
  ```bash
  who
  whoami
  ```
- **grep** (Search Text):
  ```bash
  grep "pattern" file.txt
  ```
- **last** (Display Last Logins):
  ```bash
  last
  ```
- **shutdown** (Shutdown or Restart System):
  ```bash
  shutdown -h now  # Shutdown immediately
  shutdown -r now  # Restart immediately
  ```

### Linux Directory Structure
Linux organizes files in a hierarchical directory structure:
- **/bin, /sbin, /usr/bin, /usr/sbin**: Executable binaries
- **/etc**: Configuration files
- **/home**: User directories
- **/var**: Variable data
- **/tmp**: Temporary files
- **/proc**: Process information
- **/dev**: Device files
- **/mnt, /media**: Mount points for external devices

### Working with Files and Directories
- **Creating, Viewing, and Deleting Files**:
  ```bash
  touch file.txt  # Create a new file
  cat file.txt    # View file content
  rm file.txt     # Delete a file
  ```
- **Creating, Viewing, and Deleting Directories**:
  ```bash
  mkdir directory  # Create a directory
  ls -l            # Check directory contents
  rmdir directory  # Delete an empty directory
  ```
- **Copying and Moving Files**:
  ```bash
  cp file.txt /path/to/destination  # Copy file
  mv file.txt /path/to/destination  # Move file
  ```
- **Working with Links and Inodes**:
  ```bash
  ln -s /path/to/source /path/to/symlink  # Create a symbolic link
  ls -i file.txt                          # Show inode number
  ```

### Working with File Permissions and Ownership
- **chmod** (Change File Permissions):
  ```bash
  chmod +x script.sh   # Add execute permission
  ```
- **chown** (Change File Ownership):
  ```bash
  chown user:group file.txt  # Change owner and group
  ```
