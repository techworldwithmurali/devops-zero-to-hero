## Manually - Dockerizing and Pushing to DockerHub

![Dockerizing and Pushing to DockerHub - Tech World with Murali - Moole Muralidhara Reddy.png](https://github.com/techworldwithmurali/devops-zero-to-hero/blob/main/Day-26/images/Day%20%2026-%20Dockerizing%20and%20Pushing%20to%20DockerHub%20-%20Moole%20Muralidhara%20Reddy%20-%20Tech%20World%20with%20Murali.png)

### Prerequisites:
+ Git is installed
+ Maven is installed
+ Docker is installed
+ DockerHub repository is created


### Step 1: Clone the repository
  
```xml
  github url: https://github.com/techworldwithmurali/java-application.git
```
### Step 2: build the code
```xml
mvn package
```
### Step 3: Create the repository in DockerHub
```xml
Repository Name: web-application
```
### Step 4: Write the Dockerfile
```xml
FROM tomcat:9
RUN apt update
WORKDIR /usr/local/tomcat
ADD target/*.war webapps/
EXPOSE 8080
CMD ["catalina.sh", "run"]
```
### Step 5: Build and tag the Docker image
```xml
docker build . --tag web-application:latest
docker tag web-application:latest mmreddy424/web-application:latest
```
### Step 6: Login to DockerHub in local
```xml
docker login
```
### Step 7: Push the docker image to DockerHub
```xml
docker push mmreddy424/web-application:latest
```
### Step 8: Verify whether docker image is pushed or not in DockerHub

#### Congratulations. You have successfully pushed the docker image to DockerHub.
