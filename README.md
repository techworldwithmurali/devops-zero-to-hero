# What is Docker container

A Docker container is a runtime instance of a Docker image. It encapsulates an application along with its dependencies, such as libraries, binaries, and configuration files, into a single, lightweight, executable package. Containers are isolated environments that run on top of a Docker engine or runtime, which provides the necessary operating system-level virtualization features.

### Key Characteristics of Docker Containers:

1. **Isolation**: Containers provide process isolation from other containers and the host system, ensuring that applications run independently without interference.

2. **Portability**: Containers are portable across different environments, including development, testing, and production, due to their lightweight nature and standardized format.

3. **Resource Efficiency**: Containers share the host system's kernel and resources, such as CPU, memory, and storage, making them more efficient than traditional virtual machines.

4. **Fast Deployment**: Containers can be started and stopped quickly, enabling rapid deployment and scaling of applications.

5. **Consistency**: Containers ensure consistency in application behavior across different environments by packaging everything needed to run the application into a single unit.

6. **Version Control**: Docker containers can be version-controlled and managed using Docker images, allowing for easy updates, rollbacks, and maintenance of applications.

### Use Cases of Docker Containers:

- **Microservices Architecture**: Containers are often used to deploy microservices-based applications, where each service runs in its own container.
  
- **Continuous Integration/Continuous Deployment (CI/CD)**: Containers facilitate CI/CD pipelines by providing consistent environments for building, testing, and deploying applications.

- **DevOps Practices**: Containers are integral to DevOps practices, enabling teams to deliver software faster and more reliably through automation and container orchestration tools like Kubernetes.

- **Cloud-Native Applications**: Containers are well-suited for cloud-native applications due to their scalability, agility, and resource efficiency.


### Docker Container Commands and Usage

1. **Check Running Containers**:
   - To check running containers:
     ```bash
     docker ps
     ```
   - To check both stopped and running containers:
     ```bash
     docker ps -a
     ```

2. **Get Container IDs**:
   - Get IDs of running containers:
     ```bash
     docker ps -q
     ```
   - Get IDs of both stopped and running containers:
     ```bash
     docker ps -aq
     ```

3. **Run Containers**:
   - Run a container from an image:
     ```bash
     docker container run <image_name>
     ```
   - Check running containers:
     ```bash
     docker ps
     ```
   - List all containers (including stopped ones):
     ```bash
     docker container ls
     ```

4. **Interact with Containers**:
   - Execute a command inside a running container:
     ```bash
     docker container exec <container_id or name> <command>
     ```

5. **View Container Logs and Information**:
   - View container logs:
     ```bash
     docker container logs <container_id or name>
     ```
   - Inspect container details:
     ```bash
     docker container inspect <container_id or name>
     ```

6. **Manage Containers**:
   - Rename a container:
     ```bash
     docker container rename <container_id or name> <new_name>
     ```
   - Create a container without starting it:
     ```bash
     docker container create <image_name>
     ```
   - Remove one or more containers:
     ```bash
     docker container rm <container_id>
     ```
   - Stop a running container:
     ```bash
     docker container stop <container_id>
     ```
   - Start a stopped container:
     ```bash
     docker container start <container_id>
     ```
   - Pause a running container:
     ```bash
     docker container pause <container_id>
     ```
   - Unpause a paused container:
     ```bash
     docker container unpause <container_id>
     ```
   - Wait for a container to stop:
     ```bash
     docker container wait <container_id>
     ```
   - Restart a container:
     ```bash
     docker container restart <container_id>
     ```
   - Forcefully kill a container:
     ```bash
     docker container kill <container_id>
     ```

7. **Manage Container Resources and Cleanup**:
   - Delete unused containers:
     ```bash
     docker container prune
     ```

8. **Advanced Container Operations**:
   - Create an image from a container:
     ```bash
     docker container commit <container_id> <new_image_name>
     ```
   - Copy files/directories between a container and the local filesystem:
     ```bash
     docker container cp <local_path> <container_id>:<container_path>
     ```
   - Attach local standard input, output, and error streams to a running container:
     ```bash
     docker container attach <container_id>
     ```
   - Export a container's filesystem as a tar archive:
     ```bash
     docker container export <container_id> > <container_export.tar>
     ```
   - View running processes of a container:
     ```bash
     docker container top <container_id>
     ```
   - View live stream of container resource usage statistics:
     ```bash
     docker container stats <container_id>
     ```
