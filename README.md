### Working with `rm` command
The `rm` command is used to remove or delete files and directories.

Example:
```bash
# Remove a file
rm file.txt

# Remove a directory and its contents recursively
rm -r directory/
```

### Creating and deleting users
For user management, you typically use `useradd` to add users and `userdel` to delete users.

Example:
```bash
# Add a new user
sudo useradd newuser

# Delete a user
sudo userdel newuser
```

### Creating and deleting groups
Groups are managed using `groupadd` to add groups and `groupdel` to delete groups.

Example:
```bash
# Add a new group
sudo groupadd newgroup

# Delete a group
sudo groupdel newgroup
```

### Working with `head` & `tail` commands
These commands are used to display the beginning (`head`) or end (`tail`) of files.

Example:
```bash
# Display first 10 lines of a file
head file.txt

# Display last 10 lines of a file
tail file.txt
```

### Working with `top` & `free` commands
These commands provide information about system resources (`top` for processes, `free` for memory).

Example:
```bash
# Display dynamic real-time view of processes
top

# Display memory usage statistics
free -h
```

### Working with `yum` command
`yum` is used for package management on RPM-based Linux distributions like CentOS and Red Hat.

Example:
```bash
# Install a package
sudo yum install package_name

# Remove a package
sudo yum remove package_name
```

### Working with `rpm` command
The `rpm` command is used for installing, querying, verifying, updating, and removing software packages.

Example:
```bash
# Install an RPM package
sudo rpm -i package.rpm

# Query information about an installed package
rpm -q package_name
```
