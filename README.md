### What is Waterfall Methodology?

The Waterfall methodology is a linear and sequential approach to software development. It consists of distinct phases, each following the other in a predefined order. The typical phases include:

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

1. **Iterative Development:** Developing the software in small, manageable increments.
2. **Flexibility:** Adapting to changes even late in the development process.
3. **Customer Collaboration:** Frequent communication with stakeholders to gather feedback and make adjustments.
4. **Cross-Functional Teams:** Collaborative efforts between developers, testers, and business analysts.
5. **Continuous Improvement:** Regularly reflecting on the process and seeking ways to improve.

### Difference between Waterfall & Agile Methodology

----
### What is DevOps?

DevOps is a collaboration between development and operation teams which enables continuous delivery of applications and services to our end users.

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
