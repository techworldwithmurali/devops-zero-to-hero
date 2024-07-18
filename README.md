### JFrog Artifactory Overview

**JFrog Artifactory** is a universal binary repository manager that supports all major package formats, build tools, and CI servers. It allows for efficient and secure management of artifacts from development to distribution.

**Server Specifications**:
- **CPU**: 4 CPUs
- **Memory**: 8 GB RAM
- **Ports**: 8081 (default port for Artifactory), 8082 (can be configured for other purposes)

**Artifact Types Supported**:
- JAR (Java ARchive)
- WAR (Web Application Archive)
- EAR (Enterprise Archive)
- Docker images

**Popular Artifactory Tools**:
1. **JFrog Artifactory**
2. **Sonatype Nexus**

### System Requirements

**Minimal System Requirements for JFrog Artifactory**:
- **CPU**: 4 cores
- **Memory**: 8 GB RAM
- **Disk Space**: Minimum of 100 GB (varies depending on usage)
- **Operating System**: Linux, Windows, or MacOS

**Recommended System Requirements**:
- **CPU**: 8 cores or more
- **Memory**: 16 GB RAM or more
- **Disk Space**: 200 GB or more, preferably on SSDs for better performance
- **Operating System**: Enterprise-grade Linux distributions (e.g., CentOS, Ubuntu)

### Pricing and Plans

JFrog Artifactory offers various pricing plans based on the features and support required. The plans typically include:

1. **JFrog Artifactory OSS (Open Source)**:
   - Free and open-source version.
   - Limited to a subset of features.
   - Ideal for small projects and open-source development.

2. **JFrog Artifactory Pro**:
   - Paid version with additional features.
   - Supports advanced repository management, high availability, and multi-site replication.
   - Suitable for medium to large enterprises.

3. **JFrog Artifactory Enterprise**:
   - Comprehensive solution with all the features of the Pro version plus advanced enterprise-grade capabilities.
   - Includes features like advanced security, scalability, and integration options.
   - Ideal for large-scale enterprises with complex artifact management needs.

4. **JFrog Artifactory Enterprise+**:
   - The most advanced plan, offering full access to the JFrog Platform.
   - Includes Artifactory, Xray (for security and compliance), Distribution, Pipelines, and Mission Control.
   - Designed for large organizations with extensive DevOps requirements.

**Pricing**:
- **OSS**: Free
- **Pro**: Pricing varies, typically starting at around $98/month per server
- **Enterprise**: Custom pricing based on needs and scale
- **Enterprise+**: Custom pricing, typically higher due to comprehensive features and support

For exact pricing, it is recommended to contact JFrog sales or visit their [pricing page](https://jfrog.com/pricing/).

---

## Installation of JFrog Artifactory in Linux

1. **Prepare the Server:**
   - Ensure your server meets the required specifications (4 CPUs, 8GB RAM).
   - Open ports 8081 and 8082 in your firewall.

2. **Download the JFrog Artifactory RPMs Repository File:**
   ```bash
   wget https://releases.jfrog.io/artifactory/artifactory-rpms/artifactory-rpms.repo -O jfrog-artifactory-rpms.repo
   ```

3. **Move the Repository File to the YUM Repositories Directory:**
   ```bash
   sudo mv jfrog-artifactory-rpms.repo /etc/yum.repos.d/
   ```

4. **Update YUM and Install JFrog Artifactory OSS:**
   ```bash
   sudo yum update -y && sudo yum install jfrog-artifactory-oss -y
   ```

5. **Start and Enable Artifactory Service:**
   ```bash
   sudo systemctl start artifactory
   sudo systemctl enable artifactory
   ```

6. **Verify Artifactory Status:**
   ```bash
   sudo systemctl status artifactory
   ```

7. **Access JFrog Artifactory:**
   - Open a web browser and navigate to `http://<your-server-ip>:8081/artifactory`.

8. **Configure Artifactory (Optional):**
   - Follow the on-screen setup instructions to configure your instance of JFrog Artifactory.
---

## JFrog Artifactory Dashboard Overview

The JFrog Artifactory Dashboard provides an intuitive interface for managing repositories, users, permissions, and artifacts.

### Key Functions:

- **Repository Management**: Create, manage, and configure repositories for different package types.
  
- **User and Group Management**: Define users and groups with specific permissions for accessing repositories and performing operations.
  
- **Artifact Browser**: Navigate through artifacts, view metadata, and manage artifact lifecycle.
  
- **System Health**: Monitor system health, performance metrics, and usage statistics.

---

## Creation of Users and Groups in JFrog Artifactory

JFrog Artifactory allows administrators to create users and groups to control access and permissions within the artifact repository manager.

### Steps:

1. **Access Artifactory**: Log in to the Artifactory Dashboard with administrative credentials.

2. **Navigate to Administration**: Locate the administration panel or settings section in the dashboard.

3. **Create Users**: Add new users by specifying usernames, passwords, and email addresses.

4. **Define Groups**: Create groups to assign common permissions and access rights to multiple users.

5. **Assign Permissions**: Assign permissions to users and groups based on repository access requirements.

---

## JFrog Repository Management

JFrog Artifactory provides robust repository management capabilities for organizing and storing artifacts.

### Functions:

- **Create Repositories**: Define repositories for various package types (Maven, Docker, npm, etc.).
  
- **Repository Configuration**: Configure repository settings including access control, storage quotas, and cleanup policies.
  
- **Repository Mirroring**: Set up repository mirroring and replication for high availability and disaster recovery.

---

## Integrating JFrog in Maven

**Prerequisites:**
- Java is installed.
- Maven is installed.
- Jfrog is installed.
### **Configuration:**
- Declare the Jfrog snapshot and release repositories in the pom.xml under the <distributionManagement> tag.
- To authenticate with Jfrog from Maven, declare the Jfrog username and password in the settings.xml under the <server> tag.

**pom.xml**

```xml
<distributionManagement>
    <snapshotRepository>
      <id>jfrog-snapshots</id>
      <url>http://your-host:8081/repository/maven-snapshots/</url>
    </snapshotRepository>
    <repository>
      <id>jfrog-releases</id>
      <url>http://your-host:8081/repository/maven-releases/</url>
    </repository>
  </distributionManagement>
```

**settings.xml**
```xml
  <servers>
    <server>
      <id>jfrog-releases</id>
      <username>your_username</username>
      <password>your_password</password>
    </server>
    <server>
      <id>jfrog-snapshots</id>
      <username>your_username</username>
      <password>your_password</password>
    </server>
  </servers>
```
