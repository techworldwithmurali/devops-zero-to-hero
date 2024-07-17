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

### Maven Installation (Linux)
1. **Steps**:
   - Update package index: `sudo apt update`
   - Install Maven: `sudo apt install maven`

### Maven Installation (Windows)
1. **Steps**:
   - Download Maven from [Apache Maven website](https://maven.apache.org/download.cgi).
   - Extract the archive to a directory.
   - Set `M2_HOME` environment variable.
   - Add `%M2_HOME%\bin` to `PATH` environment variable.

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
