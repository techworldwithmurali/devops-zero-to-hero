### What is Nexus

- Nexus is an open-source repository manager tool.
- It organizes, stores, and distributes artifacts required for development. With Nexus, developers can centrally control access to and deployment of every artifact within an organization, simplifying software distribution.
- The default port number for Nexus is 8081.
- Current version is 3.0+.

---

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

**Prerequisites:**
- Java is installed.
- Maven is installed.
- Nexus is installed.
### **Configuration:**
- Declare the Nexus snapshot and release repositories in the pom.xml under the <distributionManagement> tag.
- To authenticate with Nexus from Maven, declare the Nexus username and password in the settings.xml under the <server> tag.

**pom.xml**

```xml
<distributionManagement>
    <snapshotRepository>
      <id>nexus-snapshots</id>
      <url>http://your-host:8081/repository/maven-snapshots/</url>
    </snapshotRepository>
    <repository>
      <id>nexus-releases</id>
      <url>http://your-host:8081/repository/maven-releases/</url>
    </repository>
  </distributionManagement>
```

**settings.xml**
```xml
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
```
