#### INSTRUCTOR DETAILS

|  Information             | Details                                                                      |
|----------------------    |------------------------------------------------------------------------------|
| **Name**                 | Moole Muralidhara Reddy                                                      |
| **Email**                | techworldwithmurali@gmail.com                                                |
| **Website**              | https://www.techworldwithmurali.com               |
| **LinkedIn profile**     | [Moole Muralidhara Reddy](https://www.linkedin.com/in/moole-muralidhara-reddy) |

### Creating a User in Jenkins

1. **Log in to Jenkins:**
   - Open your web browser and navigate to Jenkins using your server URL (`localhost:8080` or your custom URL).

2. **Access User Management:**
   - Click on `Manage Jenkins` on the left sidebar of the Jenkins homepage.

3. **Navigate to Manage Users:**
   - Select `Manage Users`.

4. **Add a New User:**
   - Click on `Create User` from the top-left corner.

5. **Fill Out User Details:**
   - Enter the following details for the new user:
     - **Username:** sunil
     - **Password:** (Set a secure password)
     - **Confirm Password:** (Re-enter the password for confirmation)
     - Optionally, you can fill out the email address and other fields as needed.

6. **Assign User Roles (Optional):**
   - Configure any specific roles or permissions for the user if required. This can be done through Jenkins' role-based access control (RBAC) system if it's configured.

7. **Save the User:**
   - Click on `Create User` or `Save` to create the user.

----


### Setting up Role-Based Authorization Strategy in Jenkins:

1. **Install Role-Based Authorization Plugin**:
   - If not already installed, go to **Manage Jenkins > Manage Plugins > Available** and search for "Role-Based Authorization Strategy". Install the plugin and restart Jenkins if required.

2. **Configure Global Security**:
   - Go to **Manage Jenkins > Configure Global Security**.

3. **Enable Security**:
   - Check **Enable Security**.

4. **Access Control**:
   - Select **Role-Based Strategy** from the **Authorization** dropdown.

5. **Add Roles**:
   - Scroll down to **Role-Based Authorization Strategy** section.
   - Click on **Add Role** to define new roles.

6. **Define Role Permissions**:
   - For each role, define permissions based on what actions and resources users assigned to this role can access.
   - Click on **Add** to add specific permissions.
   - Choose from various permissions like **Overall**, **Job**, **Run**, **View**, etc., depending on what you want to restrict or allow.

7. **Assign Roles to Users**:
   - After defining roles and permissions, go to **Manage Jenkins > Manage Users**.
   - Click on a user to edit their details.
   - Under **Role Membership**, assign them to one or more roles defined earlier.
   - Save the changes.

8. **Test Authorization**:
   - Log out and log back in as the newly created user or other users with different roles to verify access restrictions and permissions.
----
### Understanding Master and Slave Nodes in Jenkins

In Jenkins:

- **Master Node**: The master node is the central server that manages the entire Jenkins environment. It handles job scheduling, builds, and monitoring of all activities. The master node hosts the Jenkins web interface and manages the configuration of jobs and nodes.

- **Slave Node**: A slave node, also known as an agent, is a worker machine configured to offload tasks from the master node. Slaves can be used to execute builds and other tasks, providing distributed build capabilities. They help distribute the workload and can run on different operating systems or environments than the master node.

### Setting Up a Linux Slave Node in Jenkins

To set up a Linux slave node in Jenkins, follow these steps:

#### Prerequisites

- Ensure Jenkins master is installed and running.
- Have SSH access to the Linux machine you want to configure as a slave node.

#### Steps

1. **Configure SSH Key Pair (Optional but recommended)**

   - Generate an SSH key pair on your Jenkins master server if not already done:
     ```bash
     ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
     ```
   - Copy the public key (`~/.ssh/id_rsa.pub`) to the Linux machine's `authorized_keys` file:
     ```bash
     ssh-copy-id <username>@<linux-slave-ip>
     ```
   - Test SSH connection to ensure passwordless authentication works.

2. **Install Java on Linux Slave (if not already installed)**

   - Ensure Java Development Kit (JDK) is installed on the Linux machine:
     ```bash
     sudo apt update
     sudo apt install default-jdk
     ```

3. **Prepare Jenkins Master for SSH Connection**

   - Install the necessary Jenkins plugins if not already installed:
     - SSH Agent Plugin
     - SSH Slaves Plugin

4. **Configure Linux Slave Node in Jenkins**

   - Log in to Jenkins Dashboard (Master Node).
   - Go to `Manage Jenkins` -> `Manage Nodes and Clouds` -> `New Node`.
   - Enter a node name (e.g., `Linux-Slave`).
   - Select `Permanent Agent`.
   - Configure the following details:
     - **Remote root directory**: Path where Jenkins will store files on the slave node.
     - **Labels**: Optional, used for node selection in job configurations.
     - **Launch method**: Select `Launch slave agents via SSH`.
     - **Host**: Linux slave node's IP address or hostname.
     - **Credentials**: Add SSH username and private key credentials.
     - **Host Key Verification Strategy**: Select `Non verifying Verification Strategy` if using self-signed certificates or skip host key verification.

5. **Save** the node configuration.

6. **Verify Configuration**

   - Jenkins will attempt to connect to the Linux slave node via SSH.
   - Once connected, you can start using the Linux slave node in Jenkins jobs.

----

### Setting up the Windows slave node in Jenkins

Setting up a Windows slave node in Jenkins allows you to distribute your build jobs across multiple machines, thereby improving performance and scalability. Here's a step-by-step guide to set up a Windows slave node in Jenkins:

### Prerequisites:
1. **Jenkins Master**: Ensure Jenkins master is installed and running.
2. **Windows Slave Machine**: Prepare a Windows machine that will act as the slave node.

### Steps to Set Up a Windows Slave Node in Jenkins:

1. **Install Java on the Windows Machine**:
   - Ensure Java (preferably JDK) is installed on the Windows machine. Jenkins requires Java to run.
   - Download and install Java from the official Oracle website or adopt OpenJDK.

2. **Download Jenkins Agent (Slave) JAR**:
   - On the Windows machine, download the Jenkins agent (slave) JAR file from the Jenkins server:
     - Open your Jenkins dashboard in a web browser.
     - Navigate to **Manage Jenkins > Manage Nodes > New Node**.
     - Enter a name for the node (e.g., "Windows-Slave").
     - Select **Permanent Agent** and click **OK**.
     - On the next page, under **Launch method**, select **Launch agent via Java Web Start**.
     - Click on the link to download the agent JNLP (Java Network Launch Protocol) file.

3. **Run the Jenkins Agent JAR on Windows**:
   - Open Command Prompt (cmd) on the Windows machine.
   - Navigate to the directory where you downloaded the agent JAR file.
   - Run the following command to launch the Jenkins agent:
     ```
     java -jar agent.jar -jnlpUrl <JENKINS_URL>/computer/<AGENT_NAME>/slave-agent.jnlp -secret <SECRET_KEY>
     ```
     Replace `<JENKINS_URL>`, `<AGENT_NAME>`, and `<SECRET_KEY>` with your Jenkins master URL, agent name, and secret key obtained from the Jenkins master configuration.

4. **Configure Jenkins Master**:
   - Back on your Jenkins master:
     - Go to **Manage Jenkins > Manage Nodes > New Node**.
     - Fill in the node details:
       - **Node name**: Enter the same name you used in step 2.
       - **Remote root directory**: Specify a directory on the Windows machine where Jenkins can store files.
       - **Launch method**: Select **Launch agent via Java Web Start**.
       - **Availability**: Choose how Jenkins should respond when the slave is offline or becomes online.
       - Click **Save**.

5. **Verify and Connect**:
   - After saving the node configuration, Jenkins will attempt to connect to the Windows slave.
   - If successful, the slave node should appear online in the Jenkins dashboard under **Manage Jenkins > Manage Nodes**.

6. **Additional Configuration**:
   - You can configure labels, usage restrictions, environment variables, and other settings based on your project requirements through the Jenkins node configuration interface.

### Notes:
- Ensure firewall rules allow communication between the Jenkins master and the Windows slave.
- Maintain the security of your Jenkins setup by using secure communication methods and authentication.
- Monitor the Jenkins slave node status regularly to ensure it remains online and available for build jobs.

----
### Restart and Safe Restart in Jenkins

#### Restart:
- **Purpose:** Restarting Jenkins stops the server completely and then starts it again.
- **Use Case:** Typically used after making configuration changes or installing plugins that require a full restart to take effect.
- **Procedure:**
 To restart Jenkins, you can use the following URL:

```
http://<jenkins-server>/restart
```

Replace `<jenkins-server>` with your Jenkins server's hostname or IP address.


#### Safe Restart:
- **Purpose:** Similar to restart, but allows Jenkins to finish currently running builds and tasks before restarting.
- **Use Case:** Ensures that no jobs are interrupted or left in an unstable state due to an abrupt restart.
- **Procedure:**
 To perform a safe restart (which waits for ongoing builds to complete before restarting), use the following URL:

```
http://<jenkins-server>/safeRestart
```
replace `<jenkins-server>` with your Jenkins server's hostname or IP address.

----
### Copy and Move Jobs in Jenkins

#### Copy Jobs:
- **Purpose:** Duplicates an existing job configuration, including all settings, to create a new job.
- **Use Case:** Useful for creating multiple similar jobs quickly without manually configuring each one.
- **Procedure:**
  1. Log in to Jenkins.
  2. Navigate to the job you want to copy.
  3. Click on `Copy` or `Duplicate` (depending on your Jenkins version or plugins).
  4. Provide a new name for the copied job and adjust any configurations as needed.
  5. Save the new job configuration.

#### Move Jobs:
- **Purpose:** Relocates an existing job and its configurations to a different folder or location within Jenkins.
- **Use Case:** Organizing jobs within Jenkins, especially when restructuring or cleaning up.
- **Procedure:**
  1. Log in to Jenkins.
  2. Navigate to the job you want to move.
  3. Click on `Move` or `Configure` (depending on your Jenkins version or plugins).
  4. Change the job's location by specifying a new folder path or location.
  5. Save the configuration to complete the move.
  

----

### Upstream Job

- **Definition:** An upstream job is a Jenkins job that triggers another job(s) upon its execution.
- **Function:** It initiates and precedes the execution of downstream jobs.
- **Use Case:** Typically, changes or builds in an upstream job may trigger further processes or tests in downstream jobs.
- **Configuration:** 
  - In Jenkins, you can configure an upstream job to trigger downstream jobs by using post-build actions or plugins like the Parameterized Trigger Plugin.
  - Upstream jobs do not wait for the completion of downstream jobs and proceed independently.

### Downstream Job

- **Definition:** A downstream job is a Jenkins job that is triggered by the completion or status of one or more upstream jobs.
- **Function:** It depends on the completion or status of its upstream job(s) before it can start execution.
- **Use Case:** Downstream jobs often perform tasks like deployment, integration testing, or packaging that depend on the outputs or artifacts generated by upstream jobs.
- **Configuration:** 
  - In Jenkins, downstream jobs are typically configured to trigger automatically when their upstream jobs complete successfully.
  - You can specify upstream jobs directly in the downstream job configuration to control job sequencing and dependencies.
