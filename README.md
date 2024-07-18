### What is SonarQube?

**SonarQube** is an open-source platform used for continuous inspection of code quality to perform automatic reviews with static analysis of code to detect bugs, code smells, and security vulnerabilities. 

### Key Features:

- **Code Quality Tool**: SonarQube helps in maintaining code quality and code security.
- **Open Source**: It is freely available under an open-source license, with options for commercial support and enterprise features.
- **Language Support**: Supports more than 25 programming languages including Java, C#, JavaScript, TypeScript, PHP, Python, and more.
- **Default Port**: The default port for accessing the SonarQube web interface is 9000.
- **Current LTS Version**: As of the latest update, the Long-Term Support (LTS) version is 9.9.6.
- **Java Requirement**: Requires OpenJDK 11 for running SonarQube.

### System Requirements:

- **RAM**: Minimum of 4GB RAM.
- **CPU**: Multi-core CPU recommended.
- **Disk Space**: Sufficient disk space for the storage of code analysis results (varies with the size of the codebase).

### Plans and Pricing:

SonarQube offers various plans to cater to different needs:

1. **Community Edition**:
   - **Free** and open-source.
   - Basic features for small teams and projects.
   - Suitable for open-source projects and small teams.

2. **Developer Edition**:
   - Starts at **$150 per year** for up to 5 million lines of code (LOC).
   - Advanced features including deeper analysis, additional programming languages, and branch analysis.
   - Ideal for small to medium-sized teams.

3. **Enterprise Edition**:
   - Starts at **$20,000 per year** for up to 20 million lines of code (LOC).
   - Enterprise-grade features including portfolio management, security reports, and larger LOC support.
   - Designed for medium to large enterprises.

4. **Data Center Edition**:
   - Custom pricing.
   - All features of the Enterprise Edition plus high availability, performance at scale, and advanced support options.
   - Best for large organizations with high demand for reliability and performance.

For the most accurate and up-to-date pricing, it's best to visit the [SonarQube pricing page](https://www.sonarqube.org/plans-and-pricing/) or contact SonarQube sales.

---

## How to Install SonarQube 8.9.9 on Amazon Linux

### Prerequisites:
- Your user must have sudo privileges to install packages.
- Minimum 2 VCPU & 4 GB Memory.

### Step-by-Step Installation Guide:

#### Step 1: Install OpenJDK 11 on CentOS 7 / Amazon Linux

```bash
sudo yum install java-11-amazon-corretto-devel -y
```

#### Step 1.1: Verify Java Installation

```bash
java -version
```

#### Step 2: Download SonarQube 8.9.9

```bash
cd /opt
sudo wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-8.9.9.56886.zip
```

#### Step 3: Unzip the Downloaded Archive

```bash
sudo unzip sonarqube-8.9.9.56886.zip
```

#### Step 4: Rename the SonarQube Directory

```bash
sudo mv sonarqube-8.9.9.56886 sonar
```

#### Step 5: Create a SonarQube User

```bash
sudo adduser sonar
```

#### Step 5.1: Check User Creation

```bash
sudo id sonar
```

#### Step 5.2: Change Ownership of Sonar Directory

```bash
sudo chown -R sonar:sonar sonar
```

#### Step 6: Update SonarQube Run Configuration

Edit `/opt/sonar/bin/linux-x86-64/sonar.sh` and set `RUN_AS_USER=sonar`.

#### Step 7: Start SonarQube as Sonar User

```bash
su - sonar -c "/opt/sonar/bin/linux-x86-64/sonar.sh start"
```

#### Step 8: Verify SonarQube Status

```bash
/opt/sonar/bin/linux-x86-64/sonar.sh status
```

#### Step 9: Setup SonarQube as a Service

Create `/etc/systemd/system/sonar.service`:

```ini
[Unit]
Description=SonarQube service
After=network.target

[Service]
Type=forking
LimitNOFILE=65536
User=sonar
Group=sonar
ExecStart=/opt/sonar/bin/linux-x86-64/sonar.sh start
ExecStop=/opt/sonar/bin/linux-x86-64/sonar.sh stop
Restart=always

[Install]
WantedBy=multi-user.target
```

#### Step 10: Enable and Start SonarQube Service

```bash
sudo systemctl enable sonar
sudo systemctl start sonar
```

#### Step 11: Access SonarQube Web Interface

Certainly! Here's the addition to your SonarQube installation guide:

---

### Step 11: Access SonarQube Web Interface

Ensure port 9000 is open in your firewall:

```bash
sudo firewall-cmd --permanent --zone=public --add-port=9000/tcp
sudo firewall-cmd --reload
```

#### AWS EC2 Instance Specifics:

If you are using an AWS EC2 instance, you need to open the inbound rules for port 9000 in the Security Groups associated with your instance. Here's an example:

1. Navigate to the AWS Management Console.
2. Go to the EC2 dashboard and select the Security Groups option from the left-hand menu.
3. Find the Security Group associated with your EC2 instance.
4. Edit the Inbound Rules of the Security Group to allow traffic on port 9000/tcp from your desired IP range or from anywhere as per your security requirements.

Example Inbound Rule:
- **Type:** Custom TCP Rule
- **Protocol:** TCP
- **Port Range:** 9000
- **Source:** Your IP address or 0.0.0.0/0 (for any IP)

#### Access SonarQube Web Interface

Once the Security Group rules are updated, you can access SonarQube using your server's IP or domain:

```
http://your_ip_or_domain:9000
```

#### Step 12: Initial Login

Default credentials:
- Username: admin
- Password: admin

Change the default password immediately after login.



### Conclusion

You have successfully installed SonarQube 8.9.9 on  Amazon Linux. Customize configurations and security settings as per your requirements. If you encounter any issues, feel free to seek further assistance. Happy coding!

----
## SonarQube Dashboard Overview

The SonarQube Dashboard provides a comprehensive view of code quality metrics, issues, and project health.

### Key Components:

- **Project Analysis**: Displays analysis results for each project including code smells, bugs, and vulnerabilities.
  
- **Quality Gate**: Overview of quality gate status and compliance with defined quality standards.
  
- **Issues Management**: Lists detailed issues with severity levels and recommendations for resolution.
  
- **Trends and History**: Tracks code quality trends over time and historical analysis reports.

---

## Creation of User in SonarQube

SonarQube allows administrators to create users for accessing and managing projects within the platform.

### Steps:

1. **Access SonarQube**: Log in to SonarQube with administrative credentials.

2. **Navigate to Administration**: Go to the administration panel or settings section.

3. **Create User**: Add a new user by specifying username, email, and password.

4. **Assign Permissions**: Define permissions for the user based on project access and administrative tasks.

5. **Save Changes**: Confirm user creation and permissions assignment.

----

## Integrating SonarQube in Maven

To integrate SonarQube with Maven, you can follow these steps and use the provided configuration:

1. **Add SonarQube Maven Plugin Dependency**:
   Include the SonarQube Maven plugin in your `pom.xml`:
   ```xml
   <dependency>
       <groupId>org.sonarsource.scanner.maven</groupId>
       <artifactId>sonar-maven-plugin</artifactId>
       <version>3.2</version>
   </dependency>
   ```

2. **Configure SonarQube Profile in `pom.xml`**:
   Add a profile to your `pom.xml` for SonarQube:
   ```xml
   <profiles>
       <profile>
           <id>sonar</id>
           <activation>
               <activeByDefault>true</activeByDefault>
           </activation>
           <properties>
               <!-- Optional URL to server. Default value is http://localhost:9000 -->
               <sonar.host.url>http://13.233.6.6:9000</sonar.host.url>
           </properties>
       </profile>
   </profiles>
   ```
**Note:** Update your sonarqube URL
3. **Run SonarQube Analysis with Maven**:
   Execute the SonarQube analysis using Maven with the specified properties:
   ```bash
   mvn sonar:sonar -Dsonar.host.url=http://13.233.6.6:9000 -Dsonar.login=admin -Dsonar.password=Admin@123
   ```
**Note:** Update your sonarqube username and password
This setup will integrate SonarQube with your Maven build process and allow you to perform static code analysis as part of your build.
