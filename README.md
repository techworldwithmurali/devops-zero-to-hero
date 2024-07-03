Setting up a Maven project in Jenkins involves a few straightforward steps. Here's a general outline to guide you through the process:

### Prerequisites:
1. **Jenkins Installed**: Ensure Jenkins is installed and running.
2. **Maven Installed on Jenkins**: Maven should be installed and configured on the Jenkins server. You can configure this in Jenkins Global Tool Configuration.

### Steps to Setup Maven Project in Jenkins:

1. **Create a New Jenkins Job**:
   - Open Jenkins and click on "New Item" to create a new job.
   - Enter a name for your job (e.g., "My Maven Project") and select "Freestyle project" or "Pipeline" depending on your preference.

2. **Configure Source Code Management**:
   - Under the "Source Code Management" section, choose your version control system (e.g., Git, SVN).
   - Enter the repository URL and configure credentials if required.

3. **Configure Build Triggers** (Optional):
   - Set triggers to specify when Jenkins should build your project (e.g., periodically, on SCM changes).

4. **Configure Build Environment** (Optional):
   - You can configure specific build environment variables or options under the "Build Environment" section.

5. **Configure Build Steps**:
   - In the "Build" section, add a build step to invoke Maven:
     - **Freestyle Project**: Add a "Invoke top-level Maven targets" build step. Specify the Maven version and goals (e.g., `clean install`).

6. **Save and Run the Job**:
   - Save your Jenkins job configuration.
   - Click on "Build Now" to run your Maven project for the first time.

### Example:
For a Freestyle project, the Maven build step would look like this:
- **Build > Add build step > Invoke top-level Maven targets**
  - **Maven Version**: Select the Maven installation configured in Jenkins.
  - **Goals**: Enter Maven goals such as `clean install`.
---------
Integrating Nexus with Jenkins allows you to leverage Nexus as a repository manager for storing artifacts produced by Jenkins builds. Here’s a step-by-step guide to integrate Nexus in Jenkins:

### Prerequisites:
1. **Nexus Repository Manager Installed**: Ensure Nexus is installed and running. You should have administrative access to configure repositories and access.

2. **Jenkins Installed**: Jenkins should be installed and running.

### Steps to Integrate Nexus in Jenkins:

1. **Install Nexus Artifact Uploader Plugin**:
   - In Jenkins, navigate to **Manage Jenkins > Manage Plugins > Available**.
   - Search for "Nexus Artifact Uploader" plugin and install it. This plugin allows Jenkins to upload artifacts to Nexus.

2. **Configure Nexus Credentials in Jenkins**:
   - Go to **Manage Jenkins > Manage Credentials > Jenkins > Global credentials (unrestricted)** (or a suitable domain).
   - Click on **Add Credentials**.
   - Select the appropriate kind of credentials (e.g., Username with password).
   - Enter your Nexus username and password, and provide an ID (e.g., `nexus-credentials`).

3. **Configure Nexus Repository in Jenkins Job**:
   - Open your Jenkins job (or create a new one if necessary).
   - In the job configuration:
     - **Build Environment**: Add a **Use secret text(s) or file(s)** option to specify the Nexus credentials you added earlier.
     - **Build**: Add a build step to invoke Maven or Gradle (depending on your build tool).
       - For Maven, configure the Maven goals (e.g., `clean install`).

4. **Configure Nexus Artifact Uploader**:
   - After the build step, add a post-build action:
     - **Add post-build action > Nexus Artifact Uploader**.
     - Configure the following:
       - **Nexus Instance**: Enter the Nexus server URL.
       - **Nexus Credentials**: Select the credentials you added in step 2.
       - **Repository**: Specify the repository in Nexus where artifacts should be uploaded.
       - **Artifact(s) to upload**: Define the artifacts to upload (e.g., `**/*.jar` for all JAR files).

5. **Save and Build**:
   - Save your Jenkins job configuration.
   - Click on **Build Now** to run your job and verify that artifacts are uploaded to Nexus after a successful build.

