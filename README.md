### What is Tomcat?

- Tomcat is an open source.
- It is a web server and developed by Apache software foundation.
- Apache Tomcat is purely java based application and serve java servlets , jsp pages.
- In tomcat you can deployed the war file.
- The default port number is 8080

----
### Types of Roles Available in Tomcat

In Tomcat, roles are used to define access permissions for users. Here are the common types of roles available:

1. **Manager-gui**: Allows access to the HTML interface of the Manager application.
2. **Manager-status**: Allows access to the "Server Status" page only.
3. **Manager-script**: Allows access to the text interface of the Manager application, including the ability to perform text commands.
4. **Manager-jmx**: Allows JMX proxy access to the Manager application.
5. **Admin-gui**: Allows access to the HTML interface of the Host Manager application.
6. **Admin-script**: Allows access to the text interface of the Host Manager application.

----

### How to Install Tomcat 7 in Amazon Linux

In this session, we will discuss how to install Tomcat 7 in Amazon Linux.

#### Prerequisites:
You must be logged in via SSH as a sudo or root user to install the packages.

### Step-by-Step Guide

#### Step 1: Install OpenJDK 8 in CentOS 7
```bash
sudo yum install java-1.8.0-devel -y
```

#### Step 1.1: Verify Java Installation
```bash
sudo java -version
```

#### Step 2: Download Tomcat 7
Go to the [Tomcat official page](https://archive.apache.org/dist/tomcat/tomcat-7/v7.0.106/bin/) and download the Tomcat 7.0.106 binary tar file to the `/opt` directory:
```bash
cd /opt/
wget https://archive.apache.org/dist/tomcat/tomcat-7/v7.0.106/bin/apache-tomcat-7.0.106.tar.gz
```

#### Step 3: Extract Tomcat
```bash
sudo tar -xvf apache-tomcat-7.0.106.tar.gz
```
- `x`: extract
- `v`: verbose
- `f`: file

#### Step 4: Rename the Tomcat Directory
```bash
sudo mv apache-tomcat-7.0.106 tomcat
```

#### Step 5: Create a Tomcat User
As a good security practice, it is not recommended to run Tomcat service with root privileges.

##### Step 5.1: Create the Tomcat User
```bash
sudo useradd tomcat
```

##### Step 5.2: Change Ownership of the Tomcat Directory
```bash
sudo chown -R tomcat:tomcat /opt/tomcat/
```

#### Step 6: Start Tomcat
```bash
sudo sh /opt/tomcat/bin/startup.sh
```

#### Step 7: Stop Tomcat
```bash
sudo sh /opt/tomcat/bin/shutdown.sh
```

#### Step 8: Setup Tomcat as a Service

##### Step 8.1: Create a Tomcat Service File
```bash
sudo vim /etc/systemd/system/tomcat.service
```

##### Step 8.2: Add the following content to the `tomcat.service` file:
```ini
[Unit]
Description=Tomcat 7.0.106 container
After=network.target

[Service]
Type=forking
User=tomcat
Group=tomcat
ExecStart=/opt/tomcat/bin/startup.sh
ExecStop=/opt/tomcat/bin/shutdown.sh

[Install]
WantedBy=multi-user.target
```

#### Step 9: Enable the Tomcat Service
```bash
sudo systemctl enable tomcat
```

#### Step 10: Start the Tomcat Service
```bash
sudo systemctl start tomcat
```

#### Step 11: Stop the Tomcat Service
```bash
sudo systemctl stop tomcat
```

#### Step 12: Check the Status of the Tomcat Service
```bash
sudo systemctl status tomcat
```

#### Step 13: Restart the Tomcat Service
```bash
sudo systemctl restart tomcat
```

#### Step 14: Enable Port 8080

##### For On-Premise Servers:
```bash
sudo firewall-cmd --permanent --zone=public --add-port=8080/tcp
sudo firewall-cmd --reload
```

##### For AWS EC2 Instances:
Open port 8080 in the Security Groups for the instance.

#### Step 15: Access Tomcat GUI
Open any browser and type your domain or IP address followed by port 8080:
```plaintext
http://your_ip_or_domain:8080
```

#### Step 16: Configure the Management Interface
Add users and roles in the `tomcat-users.xml` file under the `/opt/tomcat/conf/` directory.
```bash
sudo vim /opt/tomcat/conf/tomcat-users.xml
```

Add the following users and roles under the `<tomcat-users>` tag:
```xml
<role rolename="manager-gui"/>
<role rolename="manager-status"/>
<role rolename="manager-script"/>
<role rolename="manager-jmx"/>
<role rolename="admin-gui"/>
<role rolename="admin-script"/>

<user username="tomcat" password="tomcat" roles="manager-gui,admin-gui,manager-status,manager-script,manager-jmx"/>
```

#### Step 17: Restart Tomcat
```bash
sudo systemctl restart tomcat
```

### Conclusion
You have successfully installed Tomcat 7. If you face any issues during the installation, feel free to reach out in the comment box.

----
### Tomcat Dashboard Overview

The Tomcat dashboard provides a web interface to manage the server, deploy applications, and monitor server status. Here are the key sections:

1. **Server Status**: Displays the status of the server, including memory usage, threads, and request processing times.
2. **Manager App**: Allows you to deploy, undeploy, start, stop, and reload web applications.
3. **Host Manager**: Provides a way to manage virtual hosts.
4. **Server Information**: Displays detailed information about the server and the environment it's running in.

----

### Deploy WAR File in Tomcat

1. **Copy the WAR file to the Tomcat webapps directory**:
    ```bash
    cp /path/to/your/application.war /opt/tomcat/latest/webapps/
    ```

2. **Tomcat will automatically deploy the WAR file. You can verify this by checking the webapps directory for the expanded folder of your application**:
    ```bash
    ls /opt/tomcat/latest/webapps/
    ```

3. **Access your application**: 
   Open a web browser and go to `http://your-server-ip:8080/application`.
