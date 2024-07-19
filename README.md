### Difference between Containerization and Virtual Machine

### Virtualization
- **Definition**: Virtualization enables you to run multiple operating systems on the hardware of a single physical server.
- **Structure**:
  - **Infrastructure**: The physical hardware of the server.
  - **Hypervisor**: A layer that allows multiple operating systems (OS) to run on a host machine simultaneously. It manages the VMs.
  - **Guest Operating Systems**: Each VM runs its own guest OS. This could be different from the host OS.
  - **Applications**: Each VM can run different applications independently.

### Containerization
- **Definition**: Containerization enables you to deploy multiple applications using the same operating system on a single virtual machine.
- **Structure**:
  - **Infrastructure**: The physical hardware of the server.
  - **Host Operating System**: The OS installed directly on the hardware.
  - **Docker**: A containerization platform that allows applications to run in isolated environments called containers.
  - **Containerized Applications**: Applications run in containers, sharing the same OS kernel but isolated from each other.

### Key Differences
- **Operating System**: 
  - In virtualization, each VM has its own guest OS, which can be different from the host OS.
  - In containerization, all containers share the same host OS, but they run in isolated environments.
- **Resource Efficiency**:
  - Virtualization generally uses more resources because each VM requires its own OS instance.
  - Containerization is more efficient as containers share the host OS kernel and thus require fewer resources.
- **Application Deployment**:
  - Virtualization is suitable for running multiple OS instances on the same hardware.
  - Containerization is ideal for deploying multiple applications on the same OS instance, providing lightweight and consistent environments.

### Visual Representation
- **Virtual Machine Side**:
  - Applications A, B, and C each run on their own guest operating systems.
  - A hypervisor manages these guest OSs on the physical infrastructure.
- **Containerized Applications Side**:
  - Applications A, B, C, and D are running in containers.
  - Docker manages these containers on the host OS, which runs on the physical infrastructure.

----
### What is Docker?

**Docker** is an open-source platform that enables developers to build, ship, and run applications inside containers. It provides a way to automate the deployment of applications as lightweight, portable, and self-sufficient containers that can run virtually anywhere.

### Why Use Docker?

- **Portability:** Containers created with Docker can run consistently on any platform that supports Docker, from development to production environments.
- **Lightweight:** Docker containers share the host operating system kernel, making them more lightweight than VMs.
- **Fast Delivery and Scalability:** Docker containers can be quickly deployed and scaled up or down based on demand.
- **Resource Optimization:** Docker allows efficient use of system resources by running multiple containers on a single host.
- **Isolation and Security:** Containers provide isolation of applications and their dependencies, enhancing security by reducing the attack surface.

### Exploring Docker Components

**Docker Architecture Components:**
1. **Docker Client:** Used to interact with the Docker daemon (dockerd), managing containers, images, networks, and storage volumes.
2. **Docker Host (Docker Engine):** The server where the Docker daemon runs, managing container lifecycles and other Docker resources.
3. **Docker Registry:** Stores Docker images, such as Docker Hub (public registry) and private registries. Allows pulling and pushing of images.

**Other Docker Components:**
- **Docker Images:** Immutable files that serve as the basis for containers.
- **Docker Containers:** Runnable instances of Docker images.
- **Docker Network:** Networks created by Docker to facilitate communication between containers.
- **Docker Storage:** Volumes and storage drivers used by Docker to manage persistent data.

### Docker Client and Docker Host Interaction

- **Communication:** Docker client communicates with the Docker daemon (dockerd) using a REST API over UNIX sockets or network interfaces.
- **Remote Usage:** Docker client can manage Docker hosts remotely, not limited to running on the same machine as the Docker daemon.
- **Operations:** Docker client commands (like `docker run`, `docker build`, `docker pull`) instruct the Docker daemon to perform operations on containers, images, and other resources.

### Docker Registry (Docker Hub)

**Docker Hub:**
- **Public Availability:** Managed by Docker, available on the internet, and hosts publicly available Docker images.
- **Usage:** Developers can pull images from Docker Hub to their local systems or push their own images for others to use.
- **Public and Private Images:** Supports both public and private repositories based on user preferences.

**Local Docker Registry:**
- **Internal Usage:** Installed within an organization's network, acts as a local repository for Docker images.
- **Image Availability:** When pulling images, Docker first checks the local registry before resorting to Docker Hub for images not found locally.

---

### Installation of Docker in Amazon Linux

1. **Install Docker:**
   ```bash
   sudo yum install docker -y
   ```

2. **Enable Docker service:**
   ```bash
   sudo systemctl enable docker
   ```

3. **Start Docker service:**
   ```bash
   sudo systemctl start docker
   ```
   (or)
   ```bash
   sudo service docker start
   ```

4. **Stop Docker service:**
   ```bash
   sudo systemctl stop docker
   ```
   (or)
   ```bash
   sudo service docker stop
   ```

5. **Check Docker service status:**
   ```bash
   sudo systemctl status docker
   ```
   (or)
   ```bash
   sudo service docker status
   ```

6. **Restart Docker service:**
   ```bash
   sudo systemctl restart docker
   ```
   (or)
   ```bash
   sudo service docker restart
   ```

### Installation of Docker in Windows

1. **Download Docker Desktop:**
   - Go to [Docker Desktop for Windows](https://www.docker.com/products/docker-desktop) and download the installer (InstallDocker.msi).

2. **Install Docker:**
   - Double-click on InstallDocker.msi to run the installer.
   - Follow the installation wizard to accept the license, authorize the installer, and complete the installation.

3. **Start Docker:**
   - Docker starts automatically after installation.
   - If not started, you can manually start Docker from the desktop shortcut or start menu.

### Installation of Docker in Ubuntu

1. **Update package index:**
   ```bash
   sudo apt update
   ```

2. **Install Docker:**
   ```bash
   sudo apt install docker.io
   ```

3. **Enable Docker service:**
   ```bash
   sudo systemctl enable docker
   ```

4. **Start Docker service:**
   ```bash
   sudo systemctl start docker
   ```
   (or)
   ```bash
   sudo service docker start
   ```

5. **Stop Docker service:**
   ```bash
   sudo systemctl stop docker
   ```
   (or)
   ```bash
   sudo service docker stop
   ```

6. **Check Docker service status:**
   ```bash
   sudo systemctl status docker
   ```
   (or)
   ```bash
   sudo service docker status
   ```

7. **Restart Docker service:**
   ```bash
   sudo systemctl restart docker
   ```
   (or)
   ```bash
   sudo service docker restart
   ```
-----

### What is a Dockerfile?
   - A Dockerfile is a text document used to automate the process of creating Docker images.
   - It contains a series of instructions that define how to assemble a Docker image.

### Why is Dockerfile required?
   - Docker Hub offers a wide range of pre-existing Docker images.
   - However, customization of these images to meet specific requirements is often necessary.
   - Dockerfile enables users to customize and build Docker images automatically based on their specific needs.
   - This automation ensures consistency and reproducibility in deploying applications across various environments.

### Dockerfile Syntax Components:

1. **Comments:**
   - Comments in Dockerfile start with the `#` symbol.
   - They are used to annotate and explain parts of the Dockerfile for clarity.

   Example:
   ```dockerfile
   # This is a comment in a Dockerfile
   ```

2. **Instructions:**
   - Instructions are commands that Docker uses to build an image.
   - Each instruction typically starts with a keyword in uppercase (e.g., `RUN`, `FROM`, `COPY`).

   Example:
   ```dockerfile
   # Example of an instruction
   RUN echo "Hello docker!"
   ```

### Simple Example:

```dockerfile
# Dockerfile to print "Hello docker!"
RUN echo "Hello docker!"
```

In this example:
- `# Dockerfile to print "Hello docker!"` is a comment explaining the purpose of the Dockerfile.
- `RUN echo "Hello docker!"` is an instruction that tells Docker to execute the `echo "Hello docker!"` command during the image build process.


### Dockerfile Instructions:

1. **FROM:**
   - **Purpose:** Specifies the base image that your Docker image will be built upon.
   - **Examples:**
     ```dockerfile
     FROM tomcat:7
     FROM tomcat:latest
     ```
   - **Explanation:** 
     - `FROM tomcat:7` specifies the base image using the Tomcat version 7 image from Docker Hub.
     - `FROM tomcat:latest` uses the latest available Tomcat image.

2. **MAINTAINER:**
   - **Purpose:** Specifies the author or maintainer of the Docker image.
   - **Examples:**
     ```dockerfile
     MAINTAINER Administrator
     MAINTAINER admin@techworldwithmurali.com
     MAINTAINER Devops Engineer (admin@techworldwithmurali.com)
     ```
   - **Explanation:** 
     - These examples show different formats for specifying the maintainer's information.

3. **LABEL:**
   - **Purpose:** Adds metadata to the Docker image as key-value pairs.
   - **Examples:**
     ```dockerfile
     LABEL "Application_Environment"="Development Team"
     LABEL "Application_Support"="TECHWORLDWITHMURALI"
     ```
   - **Explanation:** 
     - Labels provide information about the environment or support contact for the image.

4. **ADD:**
   - **Purpose:** Copies files, directories, or remote URLs to the Docker image's filesystem.
   - **Examples:**
     ```dockerfile
     ADD /root/file /usr/local/tomcat
     ADD ["/root/file", "/usr/local/tomcat"]
     ```
   - **Explanation:** 
     - The `ADD` instruction can be used in shell form or executable form.
     - If `src` is a compressed file, it will be extracted at `dest` within the container's filesystem.

5. **COPY:**
   - **Purpose:** Copies files or directories from the Docker build context into the image's filesystem.
   - **Examples:**
     ```dockerfile
     COPY /root/file /usr/local/tomcat
     COPY ["/root/file", "/usr/local/tomcat"]
     ```
   - **Explanation:** 
     - Similar to `ADD`, `COPY` also has shell and executable forms.
     - If `src` is a compressed file, it will be copied as-is without extraction.


6. **CMD:**
   - **Purpose:** Sets the command to be executed when a container starts.
   - **Usage:**
     ```dockerfile
     CMD python myapp.py
     CMD ["python", "myapp.py"]
     ```
   - **Explanation:** 
     - Shell form (`CMD python myapp.py`): Executes the command within a shell.
     - Executable form (`CMD ["python", "myapp.py"]`): Runs the command directly without shell processing.

7. **ENTRYPOINT:**
   - **Purpose:** Configures a container to run as an executable.
   - **Usage:**
     ```dockerfile
     ENTRYPOINT ping google.com
     ENTRYPOINT python myapp.py
     ENTRYPOINT ["ping", "google.com"]
     ENTRYPOINT ["python", "myapp.py"]
     ```
   - **Explanation:** 
     - Shell form (`ENTRYPOINT ping google.com`): Executes the command within a shell.
     - Executable form (`ENTRYPOINT ["ping", "google.com"]`): Runs the command directly without shell processing.
     - If `ENTRYPOINT` is combined with `CMD`, `CMD` arguments are passed as arguments to `ENTRYPOINT`.

8. **EXPOSE:**
   - **Purpose:** Informs Docker that the container listens on specific network ports at runtime.
   - **Usage:**
     ```dockerfile
     EXPOSE 80 443
     EXPOSE 80/tcp 8080/udp
     ```
   - **Explanation:** 
     - Docker uses this information to interconnect containers and set up port redirection on the Docker host system.

9. **RUN:**
   - **Purpose:** Executes commands in a new layer on top of the current image and commits the results.
   - **Usage:**
     ```dockerfile
     RUN apt update
     ```
   - **Explanation:** 
     - Shell form (`RUN yum update`): Commands are executed within a shell.
     - Executable form (`RUN ["yum", "update"]`): Commands are run directly without shell processing.

10. **VOLUME:**
   - **Purpose:** Creates a mount point and/or assigns a volume to the container.
   - **Usage:**
     ```dockerfile
     VOLUME /opt
     VOLUME /opt:/usr/local/tomcat
     ```
   - **Explanation:** 
     - The first form (`VOLUME /opt`) creates a mount point with the specified path.
     - The second form (`VOLUME /opt:/usr/local/tomcat`) mounts a host directory (`/opt` on the host) into the container.

11. **WORKDIR:**
   - **Purpose:** Sets the working directory for any `RUN`, `CMD`, `ENTRYPOINT`, `COPY`, and `ADD` instructions.
   - **Usage:**
     ```dockerfile
     WORKDIR /usr/local/tomcat
     ```
   - **Explanation:** 
     - Specifies the directory path within the Docker container where subsequent commands are executed.

12. **ENV:**
   - **Purpose:** Sets environment variables within the Docker image.
   - **Usage:**
     ```dockerfile
     ENV APP_DIR /tmp/
     ENV app_version 3.0
     ```
   - **Explanation:** 
     - Defines environment variables that persist in the image and are available to containers created from the image.

13. **ARG:**
   - **Purpose:** Defines build-time variables that are set within the Dockerfile.
   - **Usage:**
     ```dockerfile
     ARG TMP_NAME=my_image
     ARG TMP_VER=3.0
     ```
   - **Explanation:** 
     - These variables are only available during the build process and are not persisted in the final image.

14. **USER:**
   - **Purpose:** Sets the user and optionally the user group ID for subsequent instructions.
   - **Usage:**
     ```dockerfile
     USER username
     USER username:groupname
     USER 1010
     USER 1010:1205
     ```
   - **Explanation:** 
     - Specifies the user or UID/GID under which the following commands are executed.

15. **ONBUILD:**
    - **Purpose:** Specifies a command that runs when the image is used as a base for another image.
    - **Usage:**
      ```dockerfile
      ONBUILD ADD . /opt/data
      ONBUILD RUN yum install httpd
      ```
    - **Explanation:** 
      - Commands specified with `ONBUILD` are executed when the image is used as a base for another image.

```dockerfile
# Example Dockerfile with various instructions

# Set the base image
FROM ubuntu:latest

# Maintainer information
LABEL maintainer="admin@techworldwithmurali.com"

# Set environment variables
ENV APP_DIR /app
ENV APP_VERSION 1.0

# Install dependencies
RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Set the working directory
WORKDIR $APP_DIR

# Copy application files
COPY . $APP_DIR/

# Expose ports
EXPOSE 80/tcp
EXPOSE 443/tcp

# Define default command
CMD ["python3", "app.py"]

# Example of using ARG
ARG BUILD_DATE
ARG VCS_REF
LABEL org.label-schema.build-date=$BUILD_DATE \
      org.label-schema.vcs-ref=$VCS_REF

# Example of using ENTRYPOINT
ENTRYPOINT ["python3", "app.py"]

# Example of using VOLUME
VOLUME /data

# Example of using USER
USER 1001

# Example of using ONBUILD
ONBUILD ADD . /opt/data
ONBUILD RUN apt-get update && apt-get install -y apache2

# Example of using ADD with tar.gz
ADD https://example.com/myapp.tar.gz /opt/

# Example of using ENV in executable form
ENV JAVA_HOME=/usr/lib/jvm/java-11-openjdk \
    PATH="$JAVA_HOME/bin:$PATH"

# Cleanup
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Specify the default argument for CMD
CMD ["python3", "myapp.py"]
```

### Explanation:
- **FROM:** Uses the latest Ubuntu image as the base.
- **LABEL:** Sets the maintainer's email as metadata.
- **ENV:** Defines environment variables for the application directory and version.
- **RUN:** Installs Python3, Pip, and Curl.
- **WORKDIR:** Sets the working directory for subsequent instructions.
- **COPY:** Copies the current directory's contents to the app directory in the image.
- **EXPOSE:** Exposes ports 80 and 443 for incoming traffic.
- **CMD:** Sets the default command to run when the container starts.
- **ARG:** Defines build-time arguments for labels.
- **ENTRYPOINT:** Configures the container to run as an executable with Python.
- **VOLUME:** Creates a mount point for `/data` directory.
- **USER:** Sets the user ID to 1001 for subsequent instructions.
- **ONBUILD:** Specifies commands that run when this image is used as a base for another image.
- **ADD:** Downloads and extracts a `myapp.tar.gz` file from a remote URL.
- **ENV (executable form):** Sets JAVA_HOME and updates PATH variable.
- **Cleanup:** Removes unnecessary files and cleans up the package manager cache.
