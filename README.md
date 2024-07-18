### Creating a Jenkins Job

Follow these steps to create a new Jenkins job named `sample-project`.

#### Step 1: Access Jenkins Dashboard
Open your web browser and navigate to your Jenkins instance URL:
```
http://your_ip_or_domain:8080
```
Log in with your Jenkins admin credentials.

#### Step 2: Create a New Job
1. On the Jenkins dashboard, click on **New Item** or **New Job**.
2. In the **Enter an item name** field, type `sample-project`.
3. Select **Freestyle project** or the job type you want to create.
4. Click **OK**.

#### Step 3: Configure the Job
1. **General**:
   - Add a description for your job if needed.
   
2. **Source Code Management**:
   - If you are using a version control system like Git, select **Git** and enter the repository URL and credentials.

3. **Build Triggers**:
   - Choose the appropriate triggers to start the build, such as **Build periodically** or **GitHub hook trigger for GITScm polling**.

4. **Build Environment**:
   - Select any necessary build environment options.

5. **Build**:
   - Add build steps, such as **Execute shell** or **Invoke Gradle script**, to specify the build commands or scripts.
   - Example for a shell command:
     ```bash
     echo "Building the project"
     # Add your build commands here
     ```

6. **Post-build Actions**:
   - Specify any post-build steps, such as **Publish JUnit test result report** or **Archive the artifacts**.

#### Step 4: Save the Job
1. After configuring the job, scroll down and click **Save**.

#### Step 5: Build the Job
1. On the job's page, click **Build Now** to start the build process.
2. You can view the build status and console output by clicking on the build number in the **Build History** section.

----
Here are the steps to reset the administrator password in Jenkins:

1. **Log in to your Jenkins controller.**

2. **Stop the Jenkins process.**
   ```sh
   systemctl stop jenkins
   ```

3. **Edit the Jenkins configuration file (`config.xml`).**
   - Locate the `config.xml` file inside your `jenkins/` or `$JENKINS_HOME` directory.
   - Open the `config.xml` file with a text editor.

4. **Disable security.**
   - Find the line containing `<useSecurity>true</useSecurity>`.
   - Change `true` to `false`.
   ```xml
   <useSecurity>false</useSecurity>
   ```

5. **Save the file and close the text editor.**

6. **Restart the Jenkins service.**
   ```sh
   systemctl start jenkins
   ```

7. **Sign in to Jenkins.**
   - Open your web browser and navigate to your Jenkins controller.

8. **Access Manage Jenkins.**
   - On the Jenkins dashboard, select **Manage Jenkins** from the navigation pane on the left side.

9. **Configure Global Security.**
   - On the **Manage Jenkins** page, under the **Security** section, select **Configure Global Security**.
   - Under **Security Realm**, select **Jenkins' own user database** from the dropdown menu.
   - Ensure the option **Allow users to sign up** is unchecked.
   - Save your changes.

10. **Manage Users.**
    - On the **Manage Jenkins** page, select **Users**.
    - You will see a list showing User IDs. Select the User ID that you want to change the password for.

11. **Change the password.**
    - Select **Configure** using the gear icon or the dropdown menu from the User ID.
    - Locate the **Password** section to change your password.

12. **Re-enable security (optional).**
    - After changing the password and confirming you can log in, you may want to re-enable security.
    - Edit the `config.xml` file again, changing `<useSecurity>false</useSecurity>` back to `true`.
    - Restart the Jenkins service once more.

After completing these steps, you should be able to log into your Jenkins instance again using the same username and the new password that you have just set.

----

### Setting up a Maven project in Jenkins


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

