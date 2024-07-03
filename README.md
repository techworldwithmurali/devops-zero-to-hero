### Working with `find` command
The `find` command is used to search for files in a directory hierarchy based on various criteria.

Example:
```bash
# Find all .txt files in the current directory
find . -name "*.txt"

# Find files modified in the last 7 days
find . -mtime -7
```

### Working with `df`, `du`, `kill`, `ps` commands
- `df`: Displays disk space usage of file systems.
- `du`: Shows disk usage of files and directories.
- `kill`: Terminates a process by its PID.
- `ps`: Provides information about active processes.

Examples:
```bash
# Check disk space usage
df -h

# Display disk usage of a directory
du -sh directory/

# Kill a process by PID
kill PID

# List all processes
ps aux
```

### Working with `echo`, `env`, `tac` commands
- `echo`: Prints arguments to the standard output.
- `env`: Displays environment variables.
- `tac`: Prints lines of a file in reverse order.

Examples:
```bash
# Print a message to the console
echo "Hello, World!"

# Display all environment variables
env

# Print lines of a file in reverse
tac file.txt
```

### Working with `sleep`, `exit`, `host`, `diff` commands
- `sleep`: Delays execution for a specified amount of time.
- `exit`: Terminates a script or shell with an exit status.
- `host`: Performs DNS lookups.
- `diff`: Compares files line by line.

Examples:
```bash
# Sleep for 5 seconds
sleep 5

# Exit a script with success status
exit 0

# Perform a DNS lookup
host example.com

# Compare two files
diff file1.txt file2.txt
```

### Working with `scp`, `ssh` commands
- `scp`: Securely copies files between hosts.
- `ssh`: Connects to a remote host securely.

Examples:
```bash
# Copy file from local to remote host
scp file.txt user@remote_host:/path/to/destination/

# SSH into a remote host
ssh user@remote_host
```

### Working with `crontab` & `sed` commands
- `crontab`: Manages cron jobs, scheduled tasks.
- `sed`: Stream editor for filtering and transforming text.

Examples:
```bash
# Edit the crontab file
crontab -e

# Replace text in a file using sed
sed 's/old_text/new_text/g' file.txt
```

### Working with `telnet` & `netstat` commands
- `telnet`: Communicates with another host using the Telnet protocol.
- `netstat`: Displays network connections, routing tables, interface statistics, etc.

Examples:
```bash
# Connect to a remote host via Telnet
telnet remote_host 80

# Display network connections and listening ports
netstat -antp
```

### Working with `nslookup` & `ifconfig` commands
- `nslookup`: Queries DNS for IP addresses and domain names.
- `ifconfig`: Displays or configures network interface parameters.

Examples:
```bash
# Lookup DNS information for a domain
nslookup example.com

# Display network interface details
ifconfig
```
