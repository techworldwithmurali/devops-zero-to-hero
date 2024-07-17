### Linux Overview
- Linux is an operating system.
- It is open source.
- It is similar to other operating systems such as Microsoft Windows, Apple macOS, iOS, and Google Android.
- An operating system is software that enables communication between computer hardware and software.

---
### Advantages of Linux:

- Open source
- Free
- Lightweight
- Stability
- Flexibility
- Performance
- Regular software updates
- Various distributions (distros)
- Strong networking capabilities
- Broad hardware compatibility
- Easy installation
- Active community support
----
### Linux Distributions
Linux distributions (distros) package the Linux kernel with a collection of software to create complete operating systems. Examples include:

- **Amazon Linux:** Optimized for AWS EC2, integrates seamlessly with AWS services
- **Ubuntu**: User-friendly and widely used for desktop and server environments.
- **CentOS**: Popular for servers due to its stability and long-term support.
- **Debian**: Known for its stability and package management system.
- **Fedora**: Rapidly evolving with the latest features for developers.
- **Arch Linux**: Lightweight and customizable, favored by advanced users.
----
## Linux Basic Commands

- `pwd`: Used to check the present working directory.
  ```bash
  pwd
  ```

- `cd`: Used to change the directory.
  ```bash
  cd /path/to/directory
  ```

- `ls`: Used to list the files and directories in Linux.
  ```bash
  ls
  ```

- `cal`: Used to check the calendar.
  ```bash
  cal
  ```

- `date`: Used to check the date and time.
  ```bash
  date
  ```

- `history`: Used to check the command history.
  ```bash
  history
  ```

- `clear`: Used to clear the terminal.
  ```bash
  clear
  ```

- `man`: Displays the user manual of any command.
  ```bash
  man ls
  ```

- `cat /etc/cpuinfo`: Checks CPU information in Linux.
  ```bash
  cat /etc/cpuinfo
  ```

- `cat /etc/meminfo`: Checks memory information in Linux.
  ```bash
  cat /etc/meminfo
  ```

- `ping`: Checks network connectivity.
  ```bash
  ping google.com
  ```

- `curl`: Transfers data to or from a server using various protocols.
  ```bash
  curl https://example.com
  ```

- `who`: Displays users currently logged in.
  ```bash
  who
  ```

- `who -a` (or `who -all`): Displays all details of currently logged-in users.
  ```bash
  who -a
  ```

- `who -u`: Displays the system's username.
  ```bash
  who -u
  ```

- `whoami`: Displays the current username.
  ```bash
  whoami
  ```

- `last`: Displays the list of all users logged in and out.
  ```bash
  last
  ```

- `shutdown`: Brings the system down in a secure way.
  ```bash
  shutdown -h now
  ```

----
### Linux directory structure

In Linux, the Filesystem Hierarchy Standard (FHS) defines the structure and layout of the filesystem. Here are some of the default directories commonly found under the root directory `/` according to the FHS:

![Linux directory structure 1 - Tech World with Murali - Moole Muralidhara Reddy.png](https://github.com/techworldwithmurali/devops-zero-to-hero/blob/main/Day-2/images/Day%20%202-Linux%20directory%20structure%201-%20Moole%20Muralidhara%20Reddy%20-%20Tech%20World%20with%20Murali.png)

![Linux directory structure 2 - Tech World with Murali - Moole Muralidhara Reddy.png](https://github.com/techworldwithmurali/devops-zero-to-hero/blob/main/Day-2/images/Day%20%202-%20%20Linux%20directory%20structure%202-%20Moole%20Muralidhara%20Reddy%20-%20Tech%20World%20with%20Murali.png)


1. **/bin**: Essential command binaries that are required for system operation (e.g., `ls`, `cp`, `mv`).

2. **/boot**: Static files of the bootloader.

3. **/dev**: Device files representing hardware devices (e.g., disks, printers).

4. **/etc**: Host-specific system configuration files.

5. **/home**: User home directories.

6. **/lib** and **/lib64**: Essential shared libraries and kernel modules.

7. **/media**: Mount points for removable media (e.g., USB drives).

8. **/mnt**: Temporarily mounted filesystems.

9. **/opt**: Optional application software packages.

10. **/proc**: Virtual filesystem providing process and kernel information.

11. **/root**: Home directory for the root user.

12. **/run**: Runtime data for processes.

13. **/sbin**: Essential system binaries (usually for system administration).

14. **/srv**: Data for services provided by the system.

15. **/sys**: Kernel and system information.

16. **/tmp**: Temporary files.

17. **/usr**: Secondary hierarchy containing read-only user data and programs.

18. **/var**: Variable data files (e.g., logs, spool files).

These directories help organize different types of files and provide a structured way to manage the filesystem in Linux systems.

----
### Working with files
## touch Command

The `touch` command is used to create an empty file:
```bash
touch filename.txt
```
## cat Command

The `cat` command is widely used in Linux:
- Displays the contents of a file on the standard output (stdout).
- Can be used to concatenate multiple files or redirect output.
- To view a file:
  ```bash
  cat filename.txt
  ```
- To copy contents from one file to another:
  ```bash
  cat sourcefile.txt > destinationfile.txt
  ``` 
 
## vi/vim Editor

The vi / vim editor is a popular and classic text editor in the Linux family:
- It is available in almost all Linux distributions.
- Works consistently across different platforms and distributions.
- User-friendly interface, favored by millions of Linux users for editing needs.
- Basic modes include:
  - **Insert mode**: For writing and editing text.
  - **Command mode**: For navigating, saving, and quitting.
  - **Visual mode**: For selecting and manipulating blocks of text.
  - **Escape mode**: For switching between modes and executing commands.

----

### Working with Directories

1. **Creating Directories:**
   - To create a directory named `murali`, you use:
     ```
     mkdir murali
     ```
   - To create nested directories such as `/opt/sunil/naresh/siva`:
     ```
     mkdir -p /opt/sunil/naresh/siva
     ```
   - Note the correct usage of `-p` to create parent directories if they don't exist.

### Working with `cp`

2. **Copying Files and Directories:**
   - To copy a file `murali` from `/root` to `/opt`:
     ```
     cp murali /opt
     ```
   - To copy a directory `naresh` recursively from `/root` to `/opt`:
     ```
     cp -r naresh /opt
     ```
   - Ensure `-r` is used for recursive copying of directories.

### Working with `mv`

3. **Moving or Renaming Files and Directories:**
   - To move a file `murali` from `/root` to `/opt`:
     ```
     mv murali /opt
     ```
   - To rename a file or directory `muni` to `sunil` in the same directory:
     ```
     mv muni sunil
     ```
   - The `mv` command is used for both moving and renaming.

### Working with Symbolic Links (`ln -s`)

4. **Creating Symbolic Links:**
   - To create a symbolic link `softlinkname` pointing to `originalname`:
     ```
     ln -s originalname softlinkname
     ```
   - Symbolic links can point to files or directories.

### Working with Hard Links (`ln`)

5. **Creating Hard Links:**
   - To create a hard link `hardlinkname` for `originalname`:
     ```
     ln originalname hardlinkname
     ```
   - Hard links can only be created for files, not directories.
   - They share the same inode number with the original file.

### Inode Numbers

6. **Understanding Inode Numbers:**
   - An inode number uniquely identifies each file on a Unix-like filesystem.
   - To view inode numbers with file details, you use:
     ```
     ls -li
     ```
   - The `-i` option with `ls` displays inode numbers along with other file details.
----

### File Permissions (`chmod`)

1. **Understanding Permission Notation:**
   - Permissions are represented by nine characters in Linux, where:
     - The first character (`d` in your example) indicates the type of the file (`d` for directory, `-` for regular file).
     - The next three characters (`rwx` for owner permissions).
     - The next three characters (`r-x` for group permissions).
     - The last three characters (`r-x` for others permissions).

2. **Numeric Representation of Permissions:**
   - Each permission (`r`, `w`, `x`) has a numeric value:
     - `r` (Read) = 4
     - `w` (Write) = 2
     - `x` (Execute) = 1
   - To set permissions using numeric notation:
     - Example: `chmod 777 filename`
       - Owner gets `rwx` (4+2+1 = 7)
       - Group gets `rwx` (4+2+1 = 7)
       - Others get `rwx` (4+2+1 = 7)

3. **Recursively Changing Permissions:**
   - To apply permissions recursively to all files and directories within a directory:
     ```
     chmod -R 666 directoryname/
     ```
     - This gives read (`r`) and write (`w`) permissions (`6`) to owner, group, and others.

### File Ownership (`chown`)

1. **Changing Ownership:**
   - The `chown` command changes the user and/or group ownership of files and directories.
   - Example: `chown user1:group1 filename`
     - Changes `filename` to be owned by `user1` and assigned to `group1`.
   
2. **Recursively Changing Ownership:**
   - To change ownership recursively for all files and directories within a directory:
     ```
     chown -R user:group directoryname/
     ```
     - This changes ownership to `user` and `group` for all files and directories within `directoryname`.
