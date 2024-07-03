## SonarQube Overview

SonarQube is an open-source platform for continuous inspection of code quality. It analyzes code for bugs, vulnerabilities, and code smells to ensure maintainability and reliability.

### Key Features:

- **Code Quality Analysis**: Detects bugs, vulnerabilities, and code smells in various programming languages.
  
- **Continuous Inspection**: Provides ongoing code quality checks throughout the development lifecycle.
  
- **Integration with CI/CD**: Seamless integration with Jenkins, Maven, and other CI/CD tools.
  
- **Customizable Rules**: Allows customization of quality profiles and rulesets based on project requirements.
  
- **Dashboard and Reports**: Provides visual dashboards and detailed reports on code quality metrics.

---

## How to Install SonarQube 8.9.9 on CentOS 7 / Amazon Linux

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

---

### Conclusion

You have successfully installed SonarQube 8.9.9 on CentOS 7 / Amazon Linux. Customize configurations and security settings as per your requirements. If you encounter any issues, feel free to seek further assistance. Happy coding!
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

---

## Integrating SonarQube in Maven

Integrating SonarQube with Maven facilitates automated code quality analysis and reporting during builds.

### Steps:

1. **Configure SonarQube Scanner Plugin**: Add the SonarQube scanner plugin to Maven's `pom.xml` or global `settings.xml`.

   ```xml
   <build>
     <plugins>
       <plugin>
         <groupId>org.sonarsource.scanner.maven</groupId>
         <artifactId>sonar-maven-plugin</artifactId>
         <version>3.9.1.2184</version>
       </plugin>
     </plugins>
   </build>
   ```

2. **SonarQube Configuration**: Configure SonarQube properties in Maven settings to specify SonarQube server URL, authentication details, etc.

   ```xml
   <settings>
     <servers>
       <server>
         <id>sonarqube</id>
         <username>your_username</username>
         <password>your_password</password>
       </server>
     </servers>
   </settings>
   ```

3. **Run Analysis**: Execute Maven build with SonarQube goals to trigger code analysis and send results to the SonarQube server.

   ```bash
   mvn clean install sonar:sonar
   ```

4. **View Results**: Access SonarQube dashboard to view detailed code quality reports and analysis results.
