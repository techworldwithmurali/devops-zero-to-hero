### Build Tools
1. **Definition**: Software tools that automate the process of compiling source code, packaging it, and deploying it.
2. **Purpose**: Manage dependencies, execute tests, and facilitate continuous integration and delivery (CI/CD) pipelines.

### Maven
1. **Definition**: Build automation tool primarily for Java projects.
2. **Functions**:
   - Manages project dependencies.
   - Builds and packages projects into distributable formats (e.g., JAR, WAR).
   - Provides uniform build processes via Project Object Model (POM) files (`pom.xml`).

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
