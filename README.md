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
The `sed` command, short for **Stream EDitor**, is a powerful utility in Unix-like operating systems for parsing and transforming text streams. It is commonly used for text manipulation tasks such as search and replace, editing, and filtering.

### Basic Syntax:
```
sed OPTIONS 'COMMAND' FILE
```
- **OPTIONS:** Various options to modify the behavior of `sed`.
- **COMMAND:** The operation to perform (e.g., search and replace).
- **FILE:** The input file to process.

----
