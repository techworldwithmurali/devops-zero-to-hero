### Jenkins Overview

**Jenkins** is a popular Continuous Integration/Continuous Delivery (CI/CD) tool that is open source and entirely written in Java. It is widely used for automating various stages of the software development lifecycle.

#### Key Features:
- **Open Source**: Freely available for anyone to use and modify.
- **Plugins**: Jenkins is highly extensible, with over 1000 plugins available to support building, deploying, and automating any project.
- **Cloud Support**: Jenkins supports cloud-based architecture, allowing you to deploy Jenkins on cloud platforms.
- **Default Port**: The default port number for Jenkins is 8080.

#### System Requirements:
- **Memory**: At least 4GB RAM is recommended for running Jenkins efficiently.

#### Versions:
- **Latest Version**: 2.451
- **LTS Version**: 2.440.2

### CI/CD Tools Comparison

Apart from Jenkins, there are several other CI/CD tools available:

- **Bamboo**: A CI/CD server developed by Atlassian, known for its seamless integration with other Atlassian products like Jira and Bitbucket.
- **TeamCity**: A CI/CD server from JetBrains, known for its powerful configuration capabilities and extensive support for various development practices.

### Continuous Integration (CI) Tools:

- **Jenkins**
- **Bamboo**
- **TeamCity**

# Installing Jenkins on CentOS 7

There are multiple ways to install Jenkins:

1. **Using the `yum` command**
2. **Deploying the Jenkins WAR file in Tomcat**
3. **Running the Jenkins WAR file directly**
4. **Installing Jenkins using Docker**

## 1. Using the `yum` command
You can install Jenkins using the `yum` package manager. This method is straightforward and integrates Jenkins with your system's package management.

## 2. Deploying the Jenkins WAR file in Tomcat
If you have Tomcat installed, you can deploy the Jenkins WAR file into Tomcat. This method allows you to run Jenkins as part of your existing Tomcat server.

## 3. Running the Jenkins WAR file directly
You can also run the Jenkins WAR file directly using Java. This method is quick and doesn't require a servlet container like Tomcat.

## 4. Installing Jenkins using Docker
Another way to install Jenkins is using Docker. This method allows you to run Jenkins in a container, which is isolated from your host system and easy to manage.

### Installing Jenkins on a CentOS/RHEL System Using Yum

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
