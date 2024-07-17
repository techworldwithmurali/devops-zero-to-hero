### What is ssh
The `ssh` command is used to securely connect to a remote server or machine. 

### ssh Command
- **Usage:** Connects to a remote server using the SSH protocol.
- **Syntax:** `ssh [options] [user@]hostname [command]`

### Example:
```bash
ssh -i dev.pem ec2-user@43.205.113.179
```
- `-i dev.pem`: Specifies the identity file (`dev.pem`) used for authentication. This is often a private key file (.pem) used to authenticate with the server.
- `ec2-user`: Specifies the username (`ec2-user`) to log in as on the remote server.
- `43.205.113.179`: Specifies the IP address or hostname of the remote server you want to connect to.

### Notes:
- Make sure `dev.pem` file is in the current directory or provide the full path to it.
- Replace `ec2-user` with the appropriate username if you are connecting to a different type of server (e.g., `ubuntu` for Ubuntu instances, `centos` for CentOS instances, etc.).
- Replace `43.205.113.179` with the actual IP address or hostname of the server you want to connect to.

----

### What is SCP
The `scp` (secure copy) command is used to securely copy files or directories between hosts on a network using SSH encryption. Here's how you can use `scp` to copy files both from a remote server to your local machine and from your local machine to a remote server:

### Copy from Remote Server to Local Machine

```bash
scp -i dev.pem ec2-user@43.205.113.179:/remote/path/to/file /local/path/to/destination
```

- `-i dev.pem`: Specifies the identity file (`dev.pem`) used for authentication.
- `ec2-user@43.205.113.179`: Specifies the username (`ec2-user`) and IP address or hostname of the remote server.
- `:/remote/path/to/file`: Specifies the path to the file or directory on the remote server you want to copy.
- `/local/path/to/destination`: Specifies the path on your local machine where the file or directory will be copied.

#### Example:
```bash
scp -i dev.pem ec2-user@43.205.113.179:/home/ec2-user/example.txt /home/user/Documents/
```
This command copies the `example.txt` file from the remote server located at `/home/ec2-user/`

----

### Copy from Local Machine to Remote Server
To copy files or directories from your local machine to a remote server using `scp`.

```bash
scp -i dev.pem /local/path/to/file ec2-user@43.205.113.179:/remote/path/to/destination
```

- `-i dev.pem`: Specifies the identity file (`dev.pem`) used for authentication.
- `/local/path/to/file`: Specifies the path to the file or directory on your local machine that you want to copy.
- `ec2-user@43.205.113.179`: Specifies the username (`ec2-user`) and IP address or hostname of the remote server.
- `:/remote/path/to/destination`: Specifies the path on the remote server where the file or directory will be copied.

#### Example:
```bash
scp -i dev.pem /home/user/Documents/example.txt ec2-user@43.205.113.179:/home/ec2-user/
```

This command copies the `example.txt` file from your local machine's `/home/user/Documents/` directory to the remote server located at `/home/ec2-user/`.

### Notes:
- Ensure that the path to the identity file (`-i dev.pem`) is correct and accessible from your current location.
- Replace `ec2-user` with the appropriate username for the remote server if it differs from `ec2-user`.
- Replace `43.205.113.179` with the actual IP address or hostname of the remote server.

----
### What is crontab
The `crontab` command is used to schedule tasks (commands or scripts) to run automatically at specified intervals using the cron daemon in Unix-like operating systems. Let's break down the syntax and your example:

### Crontab Syntax

The general syntax of a cron job entry is:

```
MIN HOUR DOM MON DOW CMD
```

Where:
- **MIN**: Minute (0 - 59)
- **HOUR**: Hour (0 - 23)
- **DOM**: Day of Month (1 - 31)
- **MON**: Month (1 - 12)
- **DOW**: Day of Week (0 - 6, where 0 is Sunday)
- **CMD**: Command or script to be executed

### Example

Your example:

```bash
15 * * * * /opt/script.sh
```

- **15**: Executes the command at 15 minutes past every hour.
- **\***: For the other fields (HOUR, DOM, MON, DOW), \* means any value, so the command will run every hour, every day of the month, every month, and every day of the week.
- **/opt/script.sh**: Specifies the command to run, which is `/opt/script.sh`.

### Explanation:
- This cron job will execute `/opt/script.sh` at 15 minutes past every hour, every day of the month, every month, and every day of the week.
- Make sure `/opt/script.sh` is executable (`chmod +x /opt/script.sh`) and contains the necessary commands or scripts you want to automate.

### Adding or Editing Cron Jobs

To edit or add cron jobs for the current user, use:

```bash
crontab -e
```

----
### What is sed
- The `sed` command, short for **Stream EDitor**, is a powerful utility in Unix-like operating systems for parsing and transforming text streams.
- It is commonly used for text manipulation tasks such as search and replace, editing, and filtering.

### Basic Syntax:
```
sed OPTIONS 'COMMAND' FILE
```
- **OPTIONS:** Various options to modify the behavior of `sed`.
- **COMMAND:** The operation to perform (e.g., search and replace).
- **FILE:** The input file to process.

----

### What is telnet

The `telnet` command is a network protocol that allows you to communicate with another host using the Telnet protocol, typically over a TCP/IP network. It's commonly used for remote terminal connections, but due to security concerns, it's often replaced by SSH (Secure Shell). Here's how you can use `telnet`:

### Basic Syntax:
```
telnet [OPTIONS] HOST [PORT]
```

- **HOST:** The hostname or IP address of the remote server.
- **PORT:** The port number to connect to on the remote server (default is 23 for Telnet).

### Examples:

1. **Connect to a Remote Host:**
   ```bash
   telnet example.com
   ```
   This connects to `example.com` using the default Telnet port (23).

2. **Specify a Port:**
   ```bash
   telnet example.com 8080
   ```
   This connects to `example.com` on port 8080.

3. **Additional Options:**
   - `-l`: Specify a username for the remote login.
   - `-a`: Attempt automatic login.

### Commands within Telnet Session:

Once connected, you're in a terminal session on the remote server. Here are some basic Telnet commands:

- **`open [host] [port]`:** Open a connection to the specified host and port.
- **`close` or `logout`:** Close the current Telnet session.
- **`send [text]`:** Send text to the remote server.
- **`quit`:** Close the Telnet session and exit.

----
### what is netstat
The `netstat` command is used to display network connections, routing tables, interface statistics, masquerade connections, and multicast memberships.
It's a powerful utility for network troubleshooting and monitoring. 

### Basic Syntax:
```
netstat [OPTIONS]
```

### Common `netstat` Options:

1. **-a, --all**
   - Displays all sockets (both listening and non-listening), including server sockets.
   ```bash
   netstat -a
   ```

2. **-t, --tcp**
   - Displays TCP connections.
   ```bash
   netstat -at
   ```

3. **-u, --udp**
   - Displays UDP connections.
   ```bash
   netstat -au
   ```

4. **-l, --listening**
   - Displays only listening sockets (server sockets).
   ```bash
   netstat -l
   ```

5. **-x**
   - Displays Unix socket connections.
   ```bash
   netstat -lx
   ```

6. **-s, --statistics**
   - Displays networking statistics (such as packets and errors).
   ```bash
   netstat -s
   ```

7. **-c**
   - Continuously displays information (updating every second).
   ```bash
   netstat -c
   ```

8. **--verbose**
   - Displays detailed output.
   ```bash
   netstat --verbose
   ```

9. **-r, --route**
   - Displays the kernel routing table.
   ```bash
   netstat -r
   ```

10. **-n, --numeric**
    - Shows numerical addresses instead of resolving hosts.
    ```bash
    netstat -an | grep 8080
    ```
    This command displays all connections and listening ports with their numeric addresses, and `grep 8080` filters for connections on port 8080.

### Example Usage:
- To list all TCP connections:
  ```bash
  netstat -at
  ```

- To continuously monitor network connections:
  ```bash
  netstat -c
  ```

- To display detailed statistics:
  ```bash
  netstat -s
  ```

### Note:
- Running `netstat` commands may require administrative privileges (`sudo`).
----

### What is nslookup
Nslookup ('Name Server Lookup') is a network administration command-line tool used to query DNS servers interactively and non-interactively, retrieving domain name or IP address mappings and DNS resource records (RR).

### Basic Syntax:
```
nslookup [OPTION] [NAME | -] [SERVER]
```

- **NAME:** Domain name or IP address to query.
- **SERVER:** Optional DNS server to query (if not specified, uses the default DNS server configured on your system).

### Examples:

1. **Querying an IP Address:**
   ```bash
   nslookup 8.8.8.8
   ```
   This command queries DNS to find the domain name associated with the IP address `8.8.8.8`.

2. **Querying a Domain Name:**
   ```bash
   nslookup www.example.com
   ```
   This command queries DNS to find the IP address associated with the domain `www.example.com`.
----
### What is ifconfig 
- ifconfig is a system administration utility for configuring network interfaces in Linux, primarily used to initialize interfaces during system boot.
- It offers features such as configuring, controlling, and querying TCP/IP network interface parameters.
- Common tasks include setting the IP address and netmask of any network interface, as well as enabling or disabling interfaces.

##### Viewing All Network Interfaces:
```bash
ifconfig
 ```
----

### wht is ipconfig
- The ipconfig command in Windows is used to display the current TCP/IP network configuration values, including IP address, subnet mask, default gateway, and DNS servers.
- It's a command-line tool that provides essential information about the network interface cards (NICs) installed on the system.
- This command is particularly useful for troubleshooting network connectivity issues, verifying IP configuration settings, and diagnosing network problems.

- Here are some commonly used `ipconfig` commands in Windows:

1. **Display IP Configuration for All Adapters**:
   ```
   ipconfig
   ```

2. **Display Detailed IP Configuration (including MAC address)**:
   ```
   ipconfig /all
   ```

3. **Flush DNS Resolver Cache**:
   ```
   ipconfig /flushdns
   ```
4. **Display DNS Resolver Cache**:
   ```
   ipconfig /displaydns
   ```
