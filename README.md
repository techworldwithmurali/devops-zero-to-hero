### What is Tomcat?

Apache Tomcat is an open-source web server and servlet container developed by the Apache Software Foundation. It implements the Java Servlet, JavaServer Pages (JSP), Java Expression Language, and Java WebSocket technologies. Tomcat provides a "pure Java" HTTP web server environment in which Java code can run. It's widely used for hosting Java applications and is known for its simplicity, stability, and performance.

### Types of Roles Available in Tomcat

In Tomcat, roles are used to define access permissions for users. Here are the common types of roles available:

1. **Manager-gui**: Allows access to the HTML interface of the Manager application.
2. **Manager-status**: Allows access to the "Server Status" page only.
3. **Manager-script**: Allows access to the text interface of the Manager application, including the ability to perform text commands.
4. **Manager-jmx**: Allows JMX proxy access to the Manager application.
5. **Admin-gui**: Allows access to the HTML interface of the Host Manager application.
6. **Admin-script**: Allows access to the text interface of the Host Manager application.

### Installation of Tomcat in Amazon Linux

1. **Update the system**:
    ```bash
    sudo yum update -y
    ```

2. **Install Java** (Tomcat requires Java to run):
    ```bash
    sudo yum install java-1.8.0-openjdk -y
    ```

3. **Download Apache Tomcat**:
    ```bash
    wget https://downloads.apache.org/tomcat/tomcat-9/v9.0.64/bin/apache-tomcat-9.0.64.tar.gz
    ```

4. **Extract the Tomcat package**:
    ```bash
    tar xvf apache-tomcat-9.0.64.tar.gz
    ```

5. **Move Tomcat to `/opt` directory**:
    ```bash
    sudo mv apache-tomcat-9.0.64 /opt/tomcat
    ```

6. **Change the ownership of the Tomcat directory**:
    ```bash
    sudo chown -R ec2-user:ec2-user /opt/tomcat
    ```

7. **Create a symbolic link for easier management**:
    ```bash
    sudo ln -s /opt/tomcat/apache-tomcat-9.0.64 /opt/tomcat/latest
    ```

### Tomcat Dashboard Overview

The Tomcat dashboard provides a web interface to manage the server, deploy applications, and monitor server status. Here are the key sections:

1. **Server Status**: Displays the status of the server, including memory usage, threads, and request processing times.
2. **Manager App**: Allows you to deploy, undeploy, start, stop, and reload web applications.
3. **Host Manager**: Provides a way to manage virtual hosts.
4. **Server Information**: Displays detailed information about the server and the environment it's running in.

### Setup Tomcat as a Service in Linux

1. **Create a Tomcat service file**:
    ```bash
    sudo nano /etc/systemd/system/tomcat.service
    ```

2. **Add the following content to the service file**:
    ```ini
    [Unit]
    Description=Apache Tomcat Web Application Container
    After=network.target

    [Service]
    Type=forking

    Environment=JAVA_HOME=/usr/lib/jvm/jre
    Environment=CATALINA_PID=/opt/tomcat/latest/temp/tomcat.pid
    Environment=CATALINA_HOME=/opt/tomcat/latest
    Environment=CATALINA_BASE=/opt/tomcat/latest
    Environment='CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC'
    Environment='JAVA_OPTS=-Djava.awt.headless=true -Djava.security.egd=file:/dev/./urandom'

    ExecStart=/opt/tomcat/latest/bin/startup.sh
    ExecStop=/opt/tomcat/latest/bin/shutdown.sh

    User=ec2-user
    Group=ec2-user
    UMask=0007
    RestartSec=10
    Restart=always

    [Install]
    WantedBy=multi-user.target
    ```

3. **Reload systemd to apply the changes**:
    ```bash
    sudo systemctl daemon-reload
    ```

4. **Start the Tomcat service**:
    ```bash
    sudo systemctl start tomcat
    ```

5. **Enable Tomcat to start on boot**:
    ```bash
    sudo systemctl enable tomcat
    ```

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
