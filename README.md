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

### `pom.xml`
1. **Definition**: Project Object Model XML file used by Maven.
2. **Contents**:
   - Project configuration.
   - Dependencies.
   - Plugins.
   - Build profiles.

### `settings.xml`
1. **Definition**: XML file used by Maven to configure build settings.
2. **Location**:
   - Maven installation directory (`$M2_HOME/conf/settings.xml`).
   - User's home directory (`~/.m2/settings.xml`).
3. **Configurations**:
   - Repositories.
   - Proxy settings.
   - Build profiles.

### Types of Maven Repository
1. **Local Repository**: Stores locally installed artifacts (`~/.m2/repository`).
2. **Central Repository**: Default public repository for Maven dependencies.
3. **Remote Repository**: Custom repositories for specific projects or organizations.
