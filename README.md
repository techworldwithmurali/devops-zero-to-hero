### What is Waterfall Methodology?

The Waterfall methodology is a linear and sequential approach to software development. It consists of distinct phases, each following the other in a predefined order. The typical phases include:

![Waterfall methodology - Tech World with Murali - Moole Muralidhara Reddy.png](https://github.com/techworldwithmurali/devops-zero-to-hero/blob/main/Day-1/images/Day%20%201-%20Waterfall%20methodology%20-%20Moole%20Muralidhara%20Reddy%20-%20Tech%20World%20with%20Murali.png)

1. **Requirement Analysis:** Gathering and documenting the requirements.
2. **System Design:** Creating the system architecture and design.
3. **Implementation:** Writing and compiling the code.
4. **Integration and Testing:** Combining all the parts and testing them as a whole.
5. **Deployment:** Releasing the final product to the users.
6. **Maintenance:** Performing ongoing maintenance and updates.

Each phase must be completed before moving on to the next, and there is little to no overlap between the phases.

----
### What is Agile Methodology?

Agile methodology is an iterative and incremental approach to software development that emphasizes flexibility, collaboration, and customer satisfaction. Agile involves continuous planning, testing, integration, and feedback throughout the development cycle. Key features of Agile include:

<p align="center">
  <img src="https://github.com/techworldwithmurali/devops-zero-to-hero/blob/main/Day-1/images/DevOps%20Diagram%20%20-%20Moole%20Muralidhara%20Reddy%20-%20Tech%20World%20with%20Murali.png" alt="Devops Diagaram - Tech World with Murali - Moole Muralidhara Reddy">
</p>


1. **Iterative Development:** Developing the software in small, manageable increments.
2. **Flexibility:** Adapting to changes even late in the development process.
3. **Customer Collaboration:** Frequent communication with stakeholders to gather feedback and make adjustments.
4. **Cross-Functional Teams:** Collaborative efforts between developers, testers, and business analysts.
5. **Continuous Improvement:** Regularly reflecting on the process and seeking ways to improve.

### Difference between Waterfall & Agile Methodology

![Difference bwteen Waterfall methodology and agile - Tech World with Murali - Moole Muralidhara Reddy.png](https://github.com/techworldwithmurali/devops-zero-to-hero/blob/main/Day-1/images/Day%20%201-%20Difference%20bwteen%20Waterfall%20methodology%20and%20agile%20%20-%20Moole%20Muralidhara%20Reddy%20-%20Tech%20World%20with%20Murali.png)


----
### What is DevOps?

DevOps is a collaboration between development and operation teams which enables continuous delivery of applications and services to our end users.

![ Devops Diagaram- Tech World with Murali - Moole Muralidhara Reddy.png](https://github.com/techworldwithmurali/devops-zero-to-hero/blob/main/Day-1/images/DevOps%20Diagram%20%20-%20Moole%20Muralidhara%20Reddy%20-%20Tech%20World%20with%20Murali.png)

### Benefits of DevOps

1. **Collaboration between Developers and Operations**
   - DevOps fosters a collaborative culture between development and operations teams, enhancing communication and teamwork.

2. **Error Reduction**
   - Errors can be identified and fixed at the initial stage, improving the quality and stability of applications.

3. **Reduced Implementation Time**
   - DevOps reduces the time required to implement new services from hours to minutes, accelerating the release cycle.

4. **Easy Deployment**
   - Streamlined processes and automation tools make deployment more efficient and less error-prone.

5. **Increased Customer Satisfaction**
   - Faster, more reliable releases and quicker bug fixes lead to higher customer satisfaction. A satisfied customer means more business, highlighting the importance of DevOps for organizations.
----
  ### Creating an AWS (Amazon Web Services) account

1. **Visit the AWS Website**: Go to the AWS homepage at [aws.amazon.com](https://aws.amazon.com/).

2. **Click on "Create an AWS Account"**: Look for the "Create an AWS Account" button on the AWS homepage and click on it.

3. **Provide Your Email Address**: Enter your email address. This will be used as your AWS account username.

4. **Enter Your Password**: Choose a strong password that meets AWS security requirements.

5. **Fill in Your Account Information**: Provide your full name, company name (if applicable), and contact information.

6. **Payment Information**: Enter your payment details. AWS requires a valid credit card to verify your identity, although some services may offer a free tier for new accounts.

7. **Verify Your Phone Number**: AWS will send a verification code to the phone number you provide. Enter the code to verify your identity.

8. **Choose an AWS Support Plan**: You can choose from different support plans depending on your needs. AWS offers a free basic support plan by default.

9. **Accept the AWS Customer Agreement**: Read the AWS Customer Agreement and click on the checkbox to confirm that you have read and accepted it.

10. **Click "Create Account and Continue"**: After reviewing your information, click the "Create Account and Continue" button to complete the account creation process.

11. **Confirmation**: AWS will send a verification email to the address you provided. Click the verification link in the email to activate your account.

12. **Sign In to Your AWS Account**: Once your account is activated, you can sign in to the AWS Management Console using your email address and password.

----

### Step-by-Step Guide to Create a Linux EC2 Instance:

1. **Sign in to AWS Management Console**:
   - Go to [AWS Management Console](https://aws.amazon.com/console/) and sign in with your AWS account credentials.

2. **Navigate to EC2 Dashboard**:
   - Once logged in, navigate to the EC2 service by either selecting it from the services menu or searching for "EC2" in the AWS Management Console.

3. **Launch Instance**:
   - Click on the "Instances" link in the left-hand sidebar, then click the "Launch Instance" button.

4. **Choose an Amazon Machine Image (AMI)**:
   - Select a Linux AMI of your choice (e.g., Amazon Linux 2, Ubuntu, CentOS, etc.). AWS provides several free-tier eligible AMIs that you can choose from.

5. **Choose Instance Type**:
   - Select an instance type based on your requirements. The instance type determines the virtual hardware configuration (CPU, memory, storage, etc.) of your EC2 instance.

6. **Configure Instance**:
   - Configure details such as the number of instances you want to launch, network settings (VPC, subnet, etc.), IAM role (optional), and other advanced settings like user data scripts if needed.

7. **Add Storage**:
   - Specify the size and type (e.g., General Purpose SSD, Provisioned IOPS SSD) of the root volume (boot volume) for your instance. You can also add additional EBS volumes if required.

8. **Add Tags** (Optional):
   - Add tags to your instance for better organization and management. Tags are key-value pairs that can be used for identification and resource categorization.

9. **Configure Security Group**:
   - Create a new security group or select an existing one. A security group acts as a virtual firewall that controls inbound and outbound traffic to your instance. Ensure SSH (port 22) is open to your IP address for Linux instances.

10. **Review Instance Launch**:
    - Review all the configurations you have made for your instance. Make sure everything is correct before proceeding.

11. **Launch Instance**:
    - Click the "Launch" button to launch your EC2 instance. A dialog box will prompt you to select or create a key pair. This key pair allows you to securely connect to your instance via SSH.

12. **Download Key Pair**:
    - If you don’t have an existing key pair, create a new one and download the .pem file. Store this file securely as it is required to connect to your instance.

13. **Launch Status**:
    - AWS will initiate the launch process. Once completed, you can view the status of your instance in the EC2 dashboard under "Instances".
   
----
### Downloading PuTTY and PuTTYgen:

### Downloading PuTTY (SSH Client):

1. **Visit the Official PuTTY Website**:
   - Go to the PuTTY download page at [www.putty.org](https://www.putty.org/).

2. **Download PuTTY Installer**:
   - On the PuTTY website, locate the section titled "Download PuTTY" and click on the link to download the installer package appropriate for your operating system. PuTTY is available for Windows and also has versions for Unix platforms.

3. **Run the PuTTY Installer**:
   - Once the installer file (e.g., `putty-<version>-installer.exe` for Windows) is downloaded, double-click on it to run the installer.

4. **Follow Installation Instructions**:
   - Follow the on-screen instructions to install PuTTY on your system. Typically, you will need to accept the license agreement, choose installation options, and select the installation directory.

5. **Complete the Installation**:
   - After installation completes, PuTTY should be available on your system. You can find it in the Start menu (Windows) or launch it directly from the installation directory.

### Downloading PuTTYgen (Key Generator for PuTTY):

PuTTYgen is a separate tool used to generate SSH keys for PuTTY. Here’s how to download it:

1. **Visit the Official PuTTY Website**:
   - Go back to the PuTTY download page at [www.putty.org](https://www.putty.org/).

2. **Download PuTTYgen**:
   - On the PuTTY website, find the section titled "Download PuTTYgen" and click on the link to download the PuTTYgen executable (e.g., `puttygen.exe` for Windows).

3. **Save the PuTTYgen Executable**:
   - Save the downloaded `puttygen.exe` file to a location on your computer where you can easily access it.

4. **Run PuTTYgen**:
   - Double-click on the `puttygen.exe` file to run PuTTYgen. This tool does not require installation; it runs as a standalone executable.


To convert an existing `.pem` file (like `dev.pem`) into a format that PuTTYgen can use (.ppk), follow these steps:

1. **Download PuTTYgen**:
   - If you haven't already, download PuTTYgen from the official PuTTY website: [www.putty.org](https://www.putty.org/).

2. **Open PuTTYgen**:
   - Run PuTTYgen by double-clicking on the `puttygen.exe` file you downloaded.

3. **Load Your Existing `.pem` File**:
   - In PuTTYgen, click on the "Load" button.
   - Navigate to and select your existing `.pem` file (e.g., `dev.pem`) that you want to convert.

4. **Convert and Save as `.ppk`**:
   - PuTTYgen will automatically recognize the `.pem` file format and convert it.
   - Once loaded, click on the "Save private key" button to save the converted private key in `.ppk` format.
   - Choose a secure location to save the `.ppk` file and give it a recognizable name (e.g., `dev.ppk`).
  
   ----
###  Connecting to a Linux server using PuTTY
   Connecting to a Linux server using PuTTY with a `.pem` file involves a few steps to ensure proper setup and configuration. Here’s a detailed guide on how to do it:

### Prerequisites:

1. **PuTTY and PuTTYgen**:
   - Ensure you have PuTTY and PuTTYgen installed. If not, download them from the official PuTTY website: [www.putty.org](https://www.putty.org/).

2. **SSH Key Pair (`.pem` file)**:
   - You should already have an SSH key pair in `.pem` format, such as `dev.pem`, which you downloaded or generated previously.

### Steps to Connect Using PuTTY:

1. **Convert `.pem` File to `.ppk` Format (if not done already)**:

   - Open PuTTYgen (`puttygen.exe`).
   - Click on `Load` and select your `.pem` file (`dev.pem`).
   - PuTTYgen will automatically recognize the `.pem` format.
   - Click `Save private key` to save it as a `.ppk` file (`dev.ppk`).

2. **Configure PuTTY Session**:

   - Open PuTTY (`putty.exe`).
   - In the PuTTY Configuration window:
     - Under "Session", enter your server's IP address or hostname in the "Host Name (or IP address)" field.
     - Specify the SSH port (default is 22).
     - Ensure the connection type is set to SSH.
   
3. **Configure SSH Auth with `.ppk` File**:

   - In the PuTTY Configuration window:
     - Navigate to `Connection` -> `SSH` -> `Auth`.
     - Click `Browse` and select the `.ppk` file (`dev.ppk`) you saved earlier.
   
4. **(Optional) Save the Session**:

   - Go back to the "Session" category.
   - Enter a name for your session in the "Saved Sessions" field (e.g., `MyLinuxServer`).
   - Click `Save` to save these settings for future use.
   
5. **Open the SSH Connection**:

   - Click `Open` at the bottom of the PuTTY Configuration window to initiate the SSH connection.
   - If this is your first time connecting to the server, PuTTY may ask you to confirm the server's host key. Click `Yes` to proceed.

6. **Authenticate and Login**:

   - Once connected, PuTTY will open a terminal window prompting you to login.
   - Depending on the Linux distribution, use the appropriate username:
     - For Amazon Linux: `ec2-user`
     - For Ubuntu: `ubuntu`
     - For CentOS: `centos`
   - Press `Enter` after entering the username.
   - If configured with a passphrase during the `.ppk` conversion, enter it when prompted.

7. **Connected to Your Linux Server**:

   - You are now connected to your Linux server via SSH using PuTTY. You can now execute commands and manage your server as needed.

----
### Lab Session - Creation of a Windows EC2 Instance

1. **Sign in to AWS Management Console:**
   - Navigate to the EC2 Dashboard at [AWS Management Console](https://console.aws.amazon.com/ec2/).

2. **Launch Instance:**
   - Click on "Launch Instance" to start the instance creation process.

3. **Choose AMI:**
   - In the "Step 1: Choose an Amazon Machine Image (AMI)" section, click on "AWS Marketplace" on the left sidebar.
   - Search for "Windows Server" and select a suitable Windows Server AMI. Ensure you choose a version that suits your requirements (e.g., Windows Server 2019 Base).

4. **Choose Instance Type:**
   - Select an instance type based on your requirements (e.g., t2.micro for a free-tier eligible instance). Click "Next: Configure Instance Details" when ready.

5. **Configure Instance:**
   - Configure instance details such as:
     - Number of instances to launch.
     - Network settings (usually default VPC and subnet settings are fine).
     - Optionally, configure advanced settings like IAM role, monitoring, and instance shutdown behavior. Click "Next: Add Storage" when ready.

6. **Add Storage:**
   - Specify the storage requirements for your instance. The default settings are typically sufficient for basic needs. Click "Next: Add Tags" when ready.

7. **Add Tags:**
   - Optionally, add tags to your instance for easier identification and management. Click "Next: Configure Security Group" when ready.

8. **Configure Security Group:**
   - Configure security group settings to control inbound and outbound traffic to your instance. At least allow RDP (Remote Desktop Protocol) access (port 3389) for Windows instances. You may also want to allow HTTP (port 80) or HTTPS (port 443) depending on your application needs.

9. **Review Instance Launch:**
   - Review all your instance details. Ensure everything is configured correctly. Click "Launch" when ready.

10. **Select Key Pair:**
    - In the pop-up window, select an existing key pair or create a new key pair. Note that for Windows instances, you typically do not need to use SSH keys directly. Instead, you will use RDP to connect.

11. **Access Windows Instance:**
    - Once the instance is launched, note the public IP address or DNS name of your instance from the EC2 dashboard.

12. **Connect to Windows Instance:**
    - Use Remote Desktop Protocol (RDP) to connect to your Windows instance. On your local machine:
      - Search for "Remote Desktop Connection" in the Start menu (Windows).
      - Enter the public IP address or DNS name of your instance. Click "Connect."
      - Enter the credentials (username and password) specified during instance launch.

13. **Start Using Windows Instance:**
    - You are now connected to your Windows EC2 instance. Start configuring Windows settings, installing applications, and exploring the capabilities of Windows on AWS.


### Lab Session - Creation of a Ubuntu EC2 Instance

1. **Sign in to AWS Management Console:**
   - Navigate to the EC2 Dashboard at [AWS Management Console](https://console.aws.amazon.com/ec2/).

2. **Launch Instance:**
   - Click on "Launch Instance" to start the instance creation process.

3. **Choose AMI:**
   - In the "Step 1: Choose an Amazon Machine Image (AMI)" section, search for "Ubuntu" in the search bar.
   - Select the Ubuntu AMI of your choice (e.g., Ubuntu Server 20.04 LTS).

4. **Choose Instance Type:**
   - Select an instance type based on your requirements (e.g., t2.micro for a free-tier eligible instance). Click "Next: Configure Instance Details" when ready.

5. **Configure Instance:**
   - Configure instance details such as:
     - Number of instances to launch.
     - Network settings (usually default VPC and subnet settings are fine).
     - Optionally, configure advanced settings like IAM role, monitoring, and instance shutdown behavior. Click "Next: Add Storage" when ready.

6. **Add Storage:**
   - Specify the storage requirements for your instance. The default settings are typically sufficient for basic needs. Click "Next: Add Tags" when ready.

7. **Add Tags:**
   - Optionally, add tags to your instance for easier identification and management. Click "Next: Configure Security Group" when ready.

8. **Configure Security Group:**
   - Configure security group settings to control inbound and outbound traffic to your instance. At least allow SSH (port 22) access for Linux instances. You may also want to allow HTTP (port 80) or HTTPS (port 443) depending on your application needs.

9. **Review Instance Launch:**
   - Review all your instance details. Ensure everything is configured correctly. Click "Launch" when ready.

10. **Select Key Pair:**
    - In the pop-up window, select an existing key pair or create a new key pair. Key pairs are used to securely connect to your instance via SSH.

11. **Access Instance:**
    - Once the instance is launched, note the public IP address or DNS name of your instance from the EC2 dashboard.

12. **Connect to Ubuntu Instance:**
    - Use SSH to connect to your Ubuntu instance. Open a terminal on your local machine (Linux/Mac) or use PuTTY on Windows:
      ```
      ssh -i /path/to/private-key.pem ubuntu@public-ip-address
      ```
      Replace `/path/to/private-key.pem` with the path to your private key file, `ubuntu` with the default username for Ubuntu instances, and `public-ip-address` with the public IP address of your instance.

13. **Start Using Ubuntu Instance:**
    - You are now connected to your Ubuntu EC2 instance. Start installing applications, configuring services, and exploring the capabilities of Ubuntu on AWS.
