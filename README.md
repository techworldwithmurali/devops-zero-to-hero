### Nexus Overview

- **Open Source Artifact Repository**: Nexus is an open-source repository manager that organizes, stores, and distributes artifacts crucial for development.
  
- **Centralized Artifact Management**: It enables developers to centrally manage access to and deployment of all artifacts within an organization from a unified location, simplifying software distribution.

- **Default Port**: Nexus operates on the default port number 8081.

- **Current Version**: The latest version of Nexus is 3.0+.

---

This summary highlights Nexus as a pivotal tool for managing artifacts in development environments, emphasizing its open-source nature, centralized management capabilities, default port setting, and the latest version information.
# How to Install Nexus 3 on CentOS 7 / Amazon Linux

## Prerequisites:
- Your user must have sudo privileges to install packages.
- Minimum 2 VCPU & 4 GB Memory.

## Step-by-Step Installation Guide:

### Step 1: Install OpenJDK 8 in CentOS 7 / Amazon Linux
```bash
sudo yum install java-1.8.0-devel -y
```
Check whether Java is installed:
```bash
sudo java -version
```

### Step 2: Download the Latest Nexus 3 Version
Download Nexus under `/opt` directory:
```bash
sudo wget https://download.sonatype.com/nexus/3/nexus-3.41.1-01-unix.tar.gz
```
Extract the downloaded archive:
```bash
sudo tar -xvf nexus-3.41.1-01-unix.tar.gz
```
Rename the Nexus folder:
```bash
sudo mv nexus-3.41.1-01 nexus
```

### Step 3: Create a Nexus User and Set Permissions
Create the Nexus user:
```bash
sudo adduser nexus
```
Change ownership of Nexus and `sonatype-work` directory:
```bash
sudo chown -R nexus:nexus nexus
sudo chown -R nexus:nexus sonatype-work/
```

### Step 4: Configure Nexus to Run as Non-Root User
Update Nexus user in `nexus.rc` file:
```bash
sudo vim /opt/nexus/bin/nexus.rc
# Uncomment and set run_as_user="nexus"
```

### Step 5: Configure Nexus Data Directory
Edit `nexus.vmoptions` to set data directory:
```bash
sudo vim /opt/nexus/bin/nexus.vmoptions
# Example:
# -Dkaraf.data=../sonatype-work/nexus3
```

### Step 6: Start, Stop, Restart Nexus
Start Nexus:
```bash
sudo sh /opt/nexus/bin/nexus start
```
Check Nexus status:
```bash
sudo sh /opt/nexus/bin/nexus status
```
Stop Nexus:
```bash
sudo sh /opt/nexus/bin/nexus stop
```

### Step 7: Setup Nexus as a Service (Optional)
Create `nexus.service` file:
```bash
sudo vim /etc/systemd/system/nexus.service
```
Add the following content:
```plaintext
[Unit]
Description=Nexus service
After=network.target

[Service]
Type=forking
LimitNOFILE=65536
User=nexus
Group=nexus
ExecStart=/opt/nexus/bin/nexus start
ExecStop=/opt/nexus/bin/nexus stop
Restart=always

[Install]
WantedBy=multi-user.target
```
Enable and start Nexus service:
```bash
sudo systemctl enable nexus
sudo systemctl start nexus
```

### Step 8: Access Nexus Web Interface
Open port 8081:
```bash
sudo firewall-cmd --permanent --zone=public --add-port=8081/tcp
sudo firewall-cmd --reload
```
If you are using an AWS EC2 instance, open port 8081 in Security Groups:
```plaintext
- Go to AWS EC2 Management Console.
- Navigate to Security Groups.
- Edit Inbound rules of the Security Group attached to your Nexus instance.
- Add a new rule allowing inbound traffic on port 8081 (TCP) from your IP range or any specific IP as needed.
```
Access Nexus GUI in a browser:
```
http://your_ip_or_domain:8081
```
Login using:
- Default username: admin
- Default password: (found in `/opt/sonatype-work/nexus3/admin.password`)

Follow on-screen instructions to reset the password and disable anonymous access.

## Conclusion
Congratulations! Nexus 3 is now installed on your CentOS 7 / Amazon Linux instance. If you encounter any issues, feel free to ask in the comments.

----------------
Certainly! Here's how you might structure this in a GitHub README.md format:

---

## Nexus Dashboard Overview

The Nexus Dashboard provides a comprehensive interface for managing repositories, users, and artifacts within Nexus Repository Manager.

### Key Features:

- **Repository Management**: View and manage repositories, including configuration and access settings.
- **Artifact Browser**: Navigate through artifacts stored in Nexus, inspect metadata, and download artifacts.
- **User Interface Customization**: Configure dashboard widgets and layouts based on user preferences.
- **Monitoring and Metrics**: Access repository usage statistics, health checks, and performance metrics.

---

## Creation of Users and Roles in Nexus

Nexus allows administrators to create users and define roles with specific permissions for accessing repositories and performing actions.

### Steps to Create Users and Roles:

1. **Access Nexus Dashboard**: Log in to Nexus with administrative credentials.
   
2. **Navigate to Security Settings**: Locate the security settings or administration panel in the dashboard.
   
3. **Create Users**: Add new users by specifying usernames, passwords, and email addresses.
   
4. **Define Roles**: Create roles based on specific permissions needed for repository access and operations.
   
5. **Assign Roles to Users**: Assign roles to users to control their access and capabilities within Nexus.

### Example:

```bash
# Example command to create a user in Nexus using API
curl -v -X POST -u admin:admin123 \
  -H "Content-Type: application/json" \
  -d '{"userId":"newuser", "firstName":"New", "lastName":"User", "email":"newuser@example.com", "password":"password123"}' \
  http://localhost:8081/service/rest/beta/security/users
```

---

## Integrating Nexus in Maven

Nexus integration with Maven allows seamless management of artifacts and dependencies in development workflows.

### Steps to Integrate Nexus with Maven:

1. **Configure Maven Settings**: Edit `settings.xml` located in Maven's `conf` directory.
   
2. **Add Nexus Repository**: Specify Nexus repository details including URL, username, and password in `settings.xml`.
   
3. **Build Configuration**: Update Maven build configurations to include Nexus repositories for artifact resolution and deployment.
   
4. **Testing**: Validate integration by performing Maven builds, ensuring artifacts are fetched from and deployed to Nexus repositories.

### Example `settings.xml` Configuration:

```xml
<settings>
  ...
  <servers>
    <server>
      <id>nexus-releases</id>
      <username>your_username</username>
      <password>your_password</password>
    </server>
    <server>
      <id>nexus-snapshots</id>
      <username>your_username</username>
      <password>your_password</password>
    </server>
  </servers>

  <mirrors>
    <mirror>
      <id>nexus</id>
      <mirrorOf>*</mirrorOf>
      <url>http://localhost:8081/repository/maven-public/</url>
    </mirror>
  </mirrors>
  ...
</settings>
```

