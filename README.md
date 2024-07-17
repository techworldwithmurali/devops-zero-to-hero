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
To copy files or directories from your local machine to a remote server using `scp`, you reverse the source and destination in the command. Here’s how you do it:

### Copy from Local Machine to Remote Server

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
