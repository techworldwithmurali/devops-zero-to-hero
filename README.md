# Integrating JFrog with Jenkins

### Step 1: Install Required Plugins

1. **Log in to Jenkins:**
   - Open your Jenkins dashboard.

2. **Install the JFrog Artifactory Plugin:**
   - Go to **Manage Jenkins** > **Manage Plugins**.
   - Select the **Available** tab.
   - Search for **Artifactory**.
   - Check the box next to **Artifactory Plugin** and click **Install without restart**.

3. **Install the Maven Integration Plugin:**
   - Go to **Manage Jenkins** > **Manage Plugins**.
   - Select the **Available** tab.
   - Search for **Maven Integration Plugin**.
   - Check the box next to **Maven Integration Plugin** and click **Install without restart**.

### Step 2: Configure Artifactory in Jenkins

1. **Configure Artifactory Server:**
   - Go to **Manage Jenkins** > **Configure System**.
   - Scroll down to the **JFrog Artifactory** section.
   - Click **Add Artifactory Server**.
   - Enter the **Artifactory server URL**, **Username**, and **Password**.
   - Click **Test Connection** to ensure Jenkins can communicate with Artifactory.
   - Click **Save**.

### Step 3: Configure a Jenkins Job to Use Artifactory

1. **Create a New Maven Job:**
   - On the Jenkins dashboard, click **New Item**.
   - Enter a name for your job and select **Maven Project**.
   - Click **OK**.

2. **Configure the Source Code Management (SCM):**
   - In the job configuration, go to the **Source Code Management** section.
   - Select the appropriate SCM (e.g., Git) and enter the repository URL and credentials.

2. **Configure the Build Section:**
   - Go to the **Build** section.
   - Add a **Invoke Artifactory Maven 3** build step.
   - Select your configured **Artifactory server**.
   - Specify the **Goals and options** for your Maven build (e.g., `clean install`).
   - Specify the **Release repository** and **Snapshot repository** for deploying artifacts.

3. **Deploy Artifacts to Artifactory:**
   - In the **Post-build Actions** section, add a **Deploy artifacts to Artifactory** action.
   - Select your Artifactory server.
   - Specify the target **Release repository** and **Snapshot repository**.
   - Configure additional deployment options as needed.

4. **Save and Build:**
   - Click **Save** to save the job configuration.
   - Run the job by clicking **Build Now**.

## Additional Resources

- [JFrog Artifactory Documentation](https://www.jfrog.com/confluence/display/JFROG/Artifactory)
- [Jenkins Documentation](https://www.jenkins.io/doc/)

Follow these steps to effectively integrate JFrog Artifactory with Jenkins for managing and deploying your build artifacts.

----

# Integrating SonarQube with Jenkins

[SonarQube](https://www.sonarqube.org/) is an open-source platform for continuous inspection of code quality. Integrating SonarQube with Jenkins allows you to automatically analyze and track the quality of your codebase during your CI/CD pipeline.

## Prerequisites

Before integrating SonarQube with Jenkins, ensure you have:

- SonarQube server installed and running.
- Jenkins installed and configured on your system.

## Integration Steps

### Step 1: Install SonarQube Scanner Plugin for Jenkins

1. Navigate to Jenkins Dashboard.
2. Go to `Manage Jenkins` -> `Manage Plugins`.
3. Search for `SonarQube Scanner Plugin` and install it.
4. Restart Jenkins if prompted.

### Step 2: Configure SonarQube in Jenkins

1. Go to Jenkins Dashboard.
2. Click on `Manage Jenkins` -> `Configure System`.
3. Scroll down to `SonarQube servers` section.
4. Add SonarQube server configuration:
   - Name: Give it a meaningful name.
   - Server URL: URL of your SonarQube server (e.g., `http://localhost:9000`).
   - Server authentication token: Generate a token in SonarQube and paste it here.
5. Test the connection to ensure Jenkins can communicate with SonarQube.

### Step 3: Setup Jenkins Jobs to Run SonarQube Analysis

1. Create or configure a Jenkins job for your project.
2. In the job configuration, add a build step to execute SonarQube analysis:
   - Choose `Invoke standalone SonarQube analysis` or `Invoke Gradle SonarQube analysis` depending on your build setup.
   - Configure SonarQube project key, version, and other necessary details.
3. Save the job configuration.

### Step 4: View SonarQube Analysis Results

1. As your Jenkins jobs build and execute SonarQube analysis, results will be sent to the SonarQube server.
2. Navigate to SonarQube dashboard to view detailed code quality metrics, issues, and reports.

## Additional Resources

- [SonarQube Documentation](https://docs.sonarqube.org/)
- [Jenkins Documentation](https://www.jenkins.io/doc/)

Follow these steps to effectively integrate SonarQube with Jenkins for continuous code quality analysis in your CI/CD pipeline.

----

# Deploying WAR File in Tomcat using Jenkins

[Jenkins](https://www.jenkins.io/) can automate the deployment of a WAR (Web Application Archive) file into [Apache Tomcat](http://tomcat.apache.org/) using various plugins and configurations.

## Prerequisites

Before deploying a WAR file in Tomcat using Jenkins, ensure you have:

- Jenkins installed and configured on your system.
- Apache Tomcat server installed and running.

## Deployment Steps

### Step 1: Install Deploy to Container Plugin

1. Navigate to Jenkins Dashboard.
2. Go to `Manage Jenkins` -> `Manage Plugins`.
3. Search for `Deploy to Container Plugin` and install it.
4. Restart Jenkins if prompted.

### Step 2: Configure Tomcat Server in Jenkins

1. Go to Jenkins Dashboard.
2. Click on `Manage Jenkins` -> `Configure System`.
3. Scroll down to `Deploy to container` section.
4. Add a Tomcat server configuration:
   - Select `Tomcat 7.x/8.x/9.x` depending on your installed version.
   - Enter Tomcat URL, username, and password.
   - Test the connection to ensure Jenkins can communicate with Tomcat.

### Step 3: Setup Jenkins Job to Deploy WAR File

1. Create or configure a Jenkins job for deploying your WAR file.
2. In the job configuration:
   - Add a build step to deploy WAR/EAR files to a container.
   - Choose the Tomcat server configuration you added earlier.
   - Specify the WAR/EAR file path in Jenkins workspace or provide a path to the WAR file.
   - Configure deployment context if necessary.
   - Save the job configuration.

### Step 4: Trigger Deployment

1. Build the Jenkins job to trigger the deployment process.
2. Jenkins will deploy the WAR file to Tomcat using the specified configuration.

## Additional Notes

- Ensure the WAR file is compatible with the version of Tomcat you are using.
- Verify deployment logs in Jenkins to troubleshoot any issues.

-----
# Exploring Build Periodically, Poll SCM, and Webhook in Jenkins

[Jenkins](https://www.jenkins.io/) provides several mechanisms to trigger builds based on time intervals (`build periodically`), changes in source code (`poll SCM`), and external events (`webhook`). These features are essential for automating builds and deployments in CI/CD pipelines.

## Build Periodically

The `build periodically` option in Jenkins allows you to schedule builds at specified time intervals using cron syntax.

### Setup

1. Open your Jenkins job configuration.
2. Under `Build Triggers`, select `Build periodically`.
3. Enter a cron expression to define when Jenkins should trigger builds.
   - Example: `H/15 * * * *` triggers a build every 15 minutes.
4. Save the job configuration.

## Poll SCM

The `poll SCM` option in Jenkins periodically checks the version control system (SCM) for changes and triggers a build if changes are detected.

### Setup

1. Open your Jenkins job configuration.
2. Under `Build Triggers`, select `Poll SCM`.
3. Specify a polling schedule using cron syntax.
   - Example: `*/5 * * * *` polls the SCM every 5 minutes.
4. Save the job configuration.

## Webhook

A webhook in Jenkins allows external systems (like version control systems or issue trackers) to trigger Jenkins builds automatically when specific events occur.

### Setup

1. Configure your external system (e.g., GitHub, Bitbucket) to send webhook notifications to Jenkins.
2. Open your Jenkins job configuration.
3. Under `Build Triggers`, select `GitHub hook trigger for GITScm polling` (or similar webhook trigger option based on your SCM).
4. Save the job configuration.
-----

### Installing and Configuring Email Extension Plugin in Jenkins

#### Step 1: Log in to Jenkins

1. Open your web browser and navigate to Jenkins using your server URL. For example, if Jenkins is running locally, you might use `localhost:8080` or your custom port like `localhost:9191`.
   
2. Log in with your Jenkins username and password.

#### Step 2: Install Email Extension Plugin

1. Click on `Manage Jenkins` on the left sidebar of the Jenkins homepage.

2. Select `Manage Plugins`.

3. Go to the `Available` tab in the Plugin Manager.

4. Search for "Email Extension Plugin" in the search bar.

5. Check the checkbox next to the plugin name.

6. Click on `Install without restart` (or `Download now and install after restart` if a restart is required).

#### Step 3: Configure Email Settings

1. After installing the plugin, go back to the Jenkins homepage by clicking on the Jenkins logo or `Jenkins` in the top-left corner.

2. Click on `Manage Jenkins` again.

3. Select `Configure System`.

4. Scroll down to the `Extended E-mail Notification` section.

5. Configure SMTP server settings:
   - **SMTP server**: `smtp.gmail.com` (for Gmail)
   - **Use SMTP Authentication**: Check this option.
   - **User Name**: Your Gmail username (full email address).
   - **Password**: Your Gmail password. Note: For security reasons, consider using an App Password if two-factor authentication is enabled on your Gmail account.
   - **Use SSL**: Check this option.
   - **SMTP Port**: `465`

6. Click on `Advanced...` for additional settings if needed, such as configuring proxy settings or customizing email triggers.

7. Click `Apply` and then `Save` at the bottom of the page to save your configurations.
### Stpe 4: Configure Email Notification

   - Open your Jenkins job or create a new one.
   - Click on `Configure` to edit the job settings.
   - Scroll down to `Post-build Actions`.
   - Click `Add post-build action` and select `Editable Email Notification`.

### Stpe 5: Set Up Email Settings
   - **Recipients:** Enter email addresses separated by commas.
   - **Subject:** Define a subject line for your emails.
   - **Content:** Customize the message body using Jenkins variables like `${BUILD_NUMBER}` and `${BUILD_STATUS}`.
   - **Advanced Options:** Adjust settings for triggers, attachments, and email format.

### Stpe 6: Save and Test
   - Save your Jenkins job configuration.
   - Trigger a build (`Build Now`) to test the email notification.
