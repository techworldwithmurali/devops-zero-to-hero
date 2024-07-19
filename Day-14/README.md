#### INSTRUCTOR DETAILS

|  Information             | Details                                                                      |
|----------------------    |------------------------------------------------------------------------------|
| **Name**                 | Moole Muralidhara Reddy                                                      |
| **Email**                | techworldwithmurali@gmail.com                                                |
| **Website**              | https://www.techworldwithmurali.com               |
| **LinkedIn profile**     | [Moole Muralidhara Reddy](https://www.linkedin.com/in/moole-muralidhara-reddy) |

### What is Jenkins

- **Jenkins** is a popular Continuous Integration/Continuous Delivery (CI/CD) tool that is open source and entirely written in Java.
- It is widely used for automating various stages of the software development lifecycle.

#### Key Features:
- **Open Source**: Freely available for anyone to use and modify.
- **Plugins**: Jenkins is highly extensible, with over 1000 plugins available to support building, deploying, and automating any project.
- **Cloud Support**: Jenkins supports cloud-based architecture, allowing you to deploy Jenkins on cloud platforms.
- **Default Port**: The default port number for Jenkins is 8080.

#### System Requirements:
- **Memory**: At least 4GB RAM is recommended for running Jenkins efficiently.

#### Versions:
- **Latest Version**: 2.467
- **LTS Version**: 2.452.3

### CI/CD Tools Comparison

Apart from Jenkins, there are several other CI/CD tools available:

- **Bamboo**: A CI/CD server developed by Atlassian, known for its seamless integration with other Atlassian products like Jira and Bitbucket.
- **TeamCity**: A CI/CD server from JetBrains, known for its powerful configuration capabilities and extensive support for various development practices.

### Continuous Integration (CI) Tools:

- **Jenkins**
- **Bamboo**
- **TeamCity**

# Installing Jenkins on Linux

There are multiple ways to install Jenkins:

1. **Using the `yum` command**
2. **Deploying the Jenkins WAR file in Tomcat**
3. **Running the Jenkins WAR file directly**
4. **Installing Jenkins using Docker**

----

### Installing Jenkins on Linux Using Yum

Follow these steps to install Jenkins using yum on a CentOS/RHEL system.

#### Default Port
- Jenkins runs on the default port: **8080**

#### Steps:

1. **Install Java:**
   Jenkins requires Java to run. Install Java 11 using the following command:
   ```sh
   sudo yum install java-11-amazon-corretto-devel -y
   ```

2. **Enable the Jenkins Repository:**
   Add the Jenkins repository to your system:
   ```sh
   curl --silent --location http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo | sudo tee /etc/yum.repos.d/jenkins.repo
   ```

3. **Add the Jenkins Repository Key:**
   Import the GPG key for Jenkins:
   ```sh
   sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
   ```

4. **Install Jenkins:**
   Install the Jenkins Long-Term Support (LTS) version:
   ```sh
   sudo yum install jenkins -y
   ```

5. **Enable the Jenkins Service:**
   Enable Jenkins to start at boot:
   ```sh
   sudo systemctl enable jenkins
   ```

6. **Start the Jenkins Service:**
   Start the Jenkins service:
   ```sh
   sudo systemctl start jenkins
   ```

7. **Open Port 8080 on the Firewall for On-premises server:**
   Ensure that the firewall allows traffic on port 8080:
   ```sh
   sudo firewall-cmd --permanent --zone=public --add-port=8080/tcp
   sudo firewall-cmd --reload
   ```

#### AWS EC2 Instance Example:
If you are using an AWS EC2 instance, you need to open the inbound rules for port 8080 in the Security Group associated with your instance. Here's an example:

- Navigate to the AWS Management Console.
- Go to the EC2 Dashboard and select the instance running Jenkins.
- Click on the Security tab and then on the Security Group associated with your instance.
- Edit the inbound rules to allow traffic on port 8080 (HTTP) from your desired IP ranges or from anywhere (`0.0.0.0/0` for all IP addresses).


After completing these steps, you can access Jenkins by navigating to `http://<your_server_ip>:8080` in your web browser.

----

### Jenkins Dashboard Overview

#### Jenkins Dashboard Components:

1. **Navigation Menu:**
   - Located on the left-hand side, it provides access to various Jenkins functionalities such as Jobs, Builds, Pipelines, Nodes, and more.

2. **Build Executor Status:**
   - Shows the current status of Jenkins build executors (workers or agents) and their availability.

3. **Jobs:**
   - Lists all configured Jenkins jobs, showing their status (success, failure, running) and last build status.

4. **Build Queue:**
   - Displays jobs queued up for execution, indicating waiting time and priority.

5. **Views:**
   - Allows organizing and filtering jobs into customized views for easier management.

6. **Recent Builds:**
   - Shows a summary of the most recent builds across all jobs.

7. **System Information:**
   - Provides an overview of Jenkins system information, including version, uptime, and system load.

8. **Search Box:**
   - Enables searching for specific jobs, builds, or configuration options within Jenkins.
----
### Exploring "Manage Jenkins":

Under "Manage Jenkins," you'll find various options to configure and manage Jenkins itself. Here are some key sections and options typically available:

1. **Configure System:**
   - Allows configuring global Jenkins settings such as system paths, email notification settings, security settings, and plugin configurations.

2. **Manage Plugins:**
   - Enables installing, updating, and removing Jenkins plugins. Plugins extend Jenkins functionality for various purposes like version control systems, build tools, notifications, etc.

3. **Global Tool Configuration:**
   - Allows configuring tools like JDK installations, Git, Maven, Docker, etc., globally for all Jenkins jobs.

4. **Manage Nodes and Clouds:**
   - Provides options to manage Jenkins nodes (agents/workers) and configure cloud-based agents for scaling Jenkins jobs in cloud environments.

5. **Security Configuration:**
   - Configure Jenkins security settings, including authentication, authorization, and access control.

6. **Manage Users:**
   - Add, modify, and delete user accounts in Jenkins. Set permissions and roles for each user.

7. **Script Console:**
   - Execute Groovy scripts directly on Jenkins for administrative tasks and troubleshooting.

8. **System Information:**
   - Displays detailed information about the Jenkins environment, including Java version, Jenkins version, installed plugins, and system properties.

9. **Plugin Manager:**
   - Allows managing installed plugins, including checking for updates, enabling/disabling plugins, and configuring advanced plugin options.

10. **Global Configuration Tools:**
    - Configure global tools installations for Jenkins jobs, such as Git, JDK, Gradle, and others.

----
### Installing Jenkins on Tomcat

#### Prerequisites
- **Tomcat Installed**: Ensure Tomcat is installed and configured on your server.
- **Java Installed**: Jenkins requires Java, so ensure Java JDK (preferably Java 11) is installed on your system.

#### Steps:

1. **Download Jenkins WAR file:**
   - Visit the [Jenkins WAR download page](https://www.jenkins.io/download/) and get the latest stable Jenkins WAR file (e.g., `jenkins.war`).

2. **Deploy Jenkins WAR to Tomcat:**
   - Copy the `jenkins.war` file to the Tomcat `webapps` directory. This is typically located at `$CATALINA_HOME/webapps/` where `$CATALINA_HOME` is your Tomcat installation directory.

     ```sh
     cp jenkins.war $CATALINA_HOME/webapps/
     ```

3. **Start Tomcat:**
   - Start or restart Tomcat to deploy Jenkins:
     ```sh
     sudo systemctl start tomcat   # Replace with your Tomcat start command
     ```

4. **Access Jenkins:**
   - Once Tomcat has started successfully, Jenkins should be accessible at `http://<your_server_ip>:<tomcat_port>/jenkins`.
     - Replace `<your_server_ip>` with your server's IP address.
     - Replace `<tomcat_port>` with the port configured for Tomcat (usually 8080 by default).
