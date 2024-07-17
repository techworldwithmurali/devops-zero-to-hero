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

