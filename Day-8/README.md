#### INSTRUCTOR DETAILS

|  Information             | Details                                                                      |
|----------------------    |------------------------------------------------------------------------------|
| **Name**                 | Moole Muralidhara Reddy                                                      |
| **Email**                | techworldwithmurali@gmail.com                                                |
| **Website**              | https://www.techworldwithmurali.com               |
| **LinkedIn profile**     | [Moole Muralidhara Reddy](https://www.linkedin.com/in/moole-muralidhara-reddy) |

### What is a Build Tool?

Build tools are used to build the code and generate executable applications from the source code (e.g., `.war` for a Java application). Building incorporates compiling, linking, and packaging the code into a usable or executable form.

### Types of Build Tools

There are different types of build tools available in DevOps. The main ones are:

- **Ant**
- **Maven**
- **Gradle**

----
### What is Maven?

Maven is an open-source build tool. It primarily supports Java-based applications and assists developers throughout the entire process of a software project.

### What Maven Does

### Compiling the Source Code
- Converts source code into executable bytecode.

### Packaging the Results
- Packages the compiled code into distributable formats such as JAR, WAR, or EAR files.

### Uploading Packages
- Uploads the packaged artifacts to remote repositories like Nexus or JFrog Artifactory.

----
### MobaXterm (Downloading in Windows)
1. **Purpose**: Provides a terminal with an SSH client, X11 server, and tabbed terminal for Windows.
2. **Download**: Available from the [official MobaXterm website](https://mobaxterm.mobatek.net/download.html).

----

###  Installation of Maven on Linux

### Prerequisites
- Ensure sudo privileges for your user.

### Step 1: Install OpenJDK 8
```bash
sudo yum install java-1.8.0-devel -y
```

### Step 2: Install Apache Maven
#### 2.1 Download Maven
```bash
cd /opt/
wget https://dlcdn.apache.org/maven/maven-3/3.8.6/binaries/apache-maven-3.8.6-bin.tar.gz
```

#### 2.2 Extract Maven
```bash
sudo tar -xvf apache-maven-3.8.6-bin.tar.gz
```

#### 2.3 Rename Maven Directory
```bash
sudo mv apache-maven-3.8.6 maven
```

#### 2.4 Configure Maven Environment
Create `maven.sh` in `/etc/profile.d/` and add:
```bash
export M2_HOME=/opt/maven
export PATH=${M2_HOME}/bin:${PATH}
```

#### 2.5 Set Execute Permissions
```bash
sudo chmod +x /etc/profile.d/maven.sh
```

#### 2.6 Load Configuration
```bash
source /etc/profile.d/maven.sh
```
Alternatively:
```bash
sudo source /etc/profile.d/maven.sh
```

### Step 3: Verify Installation
```bash
mvn --version
```

### Conclusion
You've successfully installed Apache Maven 3.8.6 on Amazon Linux. If any issues arise, feel free to ask for further assistance.

----

### Installation of Maven on Windows
To install Apache Maven on Windows, follow these steps:

### Step 1: Install Java
Before installing Maven, ensure Java Development Kit (JDK) is installed on your system. You can download it from [Oracle's website](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html) or use OpenJDK.

### Step 2: Download Maven
1. Go to the [Apache Maven website](https://maven.apache.org/download.cgi).
2. Download the latest Maven binary zip file to your desired location (e.g., `C:\`).

### Step 3: Unzip Maven
1. Navigate to `C:\` or the directory where you downloaded Maven.
2. Extract the contents of the Maven zip file.

### Step 4: Rename Maven Directory (Optional)
If you wish to rename the Maven directory:
- Right-click on the Maven folder.
- Select "Rename" and enter the new name (e.g., `apache-maven-3.8.6` to `maven`).

### Step 5: Set Environment Variables
1. Right-click on "This PC" or "Computer" on your desktop or File Explorer.
2. Select "Properties" → "Advanced system settings" → "Environment Variables...".
3. Under "System variables", click "New":
   - Variable name: `M2_HOME`
   - Variable value: `C:\apache-maven-3.8.6` (or your Maven installation path)

4. Find the "Path" variable in the "System variables" section, click "Edit", and add `%M2_HOME%\bin` at the end.

### Step 6: Verify Maven Installation
1. Open Command Prompt:
   - Type `cmd` in the Start menu and press Enter.

2. Check Maven version:
   ```bash
   mvn -version
   ```

This command should display Maven's version and other information if it's installed correctly.

### Conclusion
You have now installed Apache Maven on your Windows system. If you encounter any issues or have further questions, feel free to ask!

----


### What is `pom.xml`?

- POM stands for Project Object Model.
- It contains Maven project and configuration information needed to build the project, such as dependencies, build directory, source directory, test source directory, plugins, goals, etc.
- Maven reads the pom.xml file and then executes the specified goals. Before Maven 2, this file was named project.xml.
- Since Maven 2 (and in Maven 3), it has been renamed to pom.xml.


### Mandatory Elements in `pom.xml`:

1. **project**:
   - Root element that encapsulates all Maven configurations for the project.

2. **modelVersion**:
   - Specifies the version of the POM schema. For modern Maven projects, it should be set to `4.0.0`.

3. **groupId**:
   - Identifies the group or organization that the project belongs to.

4. **artifactId**:
   - Identifies the project's unique artifact (e.g., JAR, WAR) within the group.

5. **version**:
   - Specifies the version of the artifact generated by the project.

### Example `pom.xml` Structure:
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
 xsi:schemaLocation="http://maven.apache.org/POM/4.0.0   
http://maven.apache.org/xsd/maven-4.0.0.xsd"> 
 
   <modelVersion>4.0.0</modelVersion>  
  <groupId>com.techworldwithmurali</groupId>  
  <artifactId>my-first-project</artifactId>  
  <version>1</version>

</project>

```

### Explanation:
- **`modelVersion`**: Ensures compatibility with the POM schema version (`4.0.0` in this case).
- **`groupId`**: Typically follows the reversed domain name pattern to uniquely identify the project's group or organization.
- **`artifactId`**: Specifies the name of the project's artifact (e.g., JAR file) without versioning.
- **`version`**: Indicates the version of the artifact produced by the project.
----
### What is settings.xml
- The Maven settings.xml file is commonly used to define the local repository location, alternate remote repository servers, and authentication information for private repositories.
For example:
- Nexus username and password can be declared within the <server> tag inside the settings.xml.
### settings.xml location

- Maven can utilize two settings.xml files simultaneously:
- Maven installation directory:
- $M2_HOME/conf/settings.xml (global settings)
- User's home directory:
- ${user.home}/.m2/settings.xml (user settings)
- Both files are optional. If both files are present, the values in the user home settings file override the values from the global settings file.

----
### Types of Maven Repository
- A Maven repository is a directory containing packaged JAR files along with their corresponding pom.xml files.
- Maven searches for dependencies in these repositories.
- There are three types of Maven repositories:
### Local Repository:
 - This repository is on the developer's local machine and stores all dependencies that have been downloaded.
### Central Repository:
 - The default repository used by Maven, maintained by the Maven community. It contains a vast number of commonly used libraries.
### Remote Repository:
 - Any other repository accessed over the network, typically used for sharing internal or proprietary libraries across a team or organization.

![ Types of Maven Repository- Tech World with Murali - Moole Muralidhara Reddy.png](https://github.com/techworldwithmurali/devops-zero-to-hero/blob/main/Day-8/images/Day%20%208-%20%20Types%20of%20Maven%20Repository-%20Moole%20Muralidhara%20Reddy%20-%20Tech%20World%20with%20Murali.png)
