#### INSTRUCTOR DETAILS

|  Information             | Details                                                                      |
|----------------------    |------------------------------------------------------------------------------|
| **Name**                 | Moole Muralidhara Reddy                                                      |
| **Email**                | techworldwithmurali@gmail.com                                                |
| **Website**              | https://www.techworldwithmurali.com               |
| **LinkedIn profile**     | [Moole Muralidhara Reddy](https://www.linkedin.com/in/moole-muralidhara-reddy) |


### Build & Deploy to Tomcat usinge Jenkins Declarative Pipeline 
This  Jenkins Pipeline script is designed to clone a Git repository, build the Java application using Maven, and deploy the built WAR file to Apache Tomcat.

![Build and Deploy to Tomcat - Tech World with Murali - Moole Muralidhara Reddy.png](https://github.com/techworldwithmurali/devops-zero-to-hero/blob/main/Day-19/images/Day%20%2019-Build%20and%20%20Deploy%20to%20Tomcat%20%20-%20Moole%20Muralidhara%20Reddy%20-%20Tech%20World%20with%20Murali.png)


```groovy
pipeline {
    agent any
    
    tools {
        // Define Maven tool installation
        maven "Maven-3.9.6"
    }
    
    options {
        timestamps() // Adds timestamps to the console output
        buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '5', numToKeepStr: '2')) // Configure build discard settings
        disableConcurrentBuilds() // Ensures that only one build executes at a time for this pipeline
    }
    
    stages {
        stage('Clone the repo') {
            steps {
                // Checkout code from Git repository
                git branch: 'main', credentialsId: 'Github_credentails', url: 'https://github.com/MooleMuraliDharaReddy/java-app.git'
            }
        }
        
        stage('Build the code') {
            steps {
                // Build project using Maven
                sh 'mvn clean install'
            }
        }
        
        stage('Deploy the application in Tomcat') {
            steps {
                // Deploy WAR file to Tomcat
                deploy adapters: [tomcat9(credentialsId: 'Tomcat-credentails', url: 'http://3.95.5.158:8080')], 
                       war: '**/*.war'
            }
        }
    }
}
```

### Explanation:

- **Agent:** `agent any` specifies that this pipeline can execute on any available agent in Jenkins.
  
- **Tools:** `maven "Maven-3.9.6"` ensures that the pipeline uses Maven version 3.9.6 for building the project. Make sure this matches the tool installation name in Jenkins Global Tool Configuration.

- **Options:**
  - `timestamps()`: Adds timestamps to the console output for each build step.
  - `buildDiscarder`: Configures the build discard strategy to keep builds for 5 days and retain a maximum of 2 builds.
  - `disableConcurrentBuilds()`: Prevents concurrent builds of this pipeline to avoid conflicts.

- **Stages:**
  - **Clone the repo:** Uses the Git plugin to checkout the code from the specified GitHub repository.
  - **Build the code:** Executes Maven command `mvn clean install` to build the Maven project.
  - **Deploy the application in Tomcat:** Uses the Tomcat Deploy plugin (`deploy`) to deploy the built WAR artifact to Apache Tomcat.

### Notes:
- Ensure that the credentials (`Github_credentails` and `Tomcat-credentails`) are correctly configured in Jenkins Credentials Manager with appropriate permissions.
- Replace placeholders (`http://3.95.5.158:8080`) with the actual URL of your Tomcat server.
- Adjust `war: '**/*.war'` according to your project's WAR file name and location after the Maven build.

----
#### Store the Jenkinsfile in GitHub.
