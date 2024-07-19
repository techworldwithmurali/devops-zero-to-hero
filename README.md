#### INSTRUCTOR DETAILS

|  Information             | Details                                                                      |
|----------------------    |------------------------------------------------------------------------------|
| **Name**                 | Moole Muralidhara Reddy                                                      |
| **Email**                | techworldwithmurali@gmail.com                                                |
| **Website**              | https://www.techworldwithmurali.com               |
| **LinkedIn profile**     | [Moole Muralidhara Reddy](https://www.linkedin.com/in/moole-muralidhara-reddy) |

### What is Jenkins Pipeline?

- In simple terms, a Jenkins Pipeline is a collection of plugins that help you create and manage continuous delivery workflows using Jenkins.
- It provides an automation server where you can define and execute delivery pipelines using a specialized scripting language called pipeline DSL (Domain-specific Language).
- his allows you to create both straightforward and intricate pipelines directly within Jenkins, treating your pipeline configuration as code.


### Jenkinsfile

- A Jenkinsfile is a text file that defines the pipeline workflow as code.
- It allows you to automate the building, testing, and deployment of your software projects.

### Benefits of Using Jenkinsfile

- **Automation:** Jenkinsfile enables automated pipeline creation across all branches and facilitates handling pull requests with a single configuration.
- **Review and Audit:** It provides visibility by allowing you to review and audit your pipeline configuration directly within the Jenkinsfile.
- **Single Source of Truth:** Jenkinsfile serves as the authoritative source for your pipeline configuration, editable by multiple users.
- **Configuration Flexibility:** You can define Jenkinsfile configurations either through the Jenkins web UI or directly in the file itself.

### Types of Syntax in Jenkinsfile

There are two main syntaxes used for defining Jenkins Pipeline in a Jenkinsfile:

#### 1. Declarative Pipeline

- **Purpose**: Offers a simpler and more structured way of defining pipelines.
- **Introduced**: Supported in Jenkins Pipeline plugin version 2.5 and later.
- **Syntax**: Must be enclosed within a `pipeline` block.
  
  Example:
  ```groovy
  pipeline {
      // Declarative Pipeline steps here
  }
  ```

#### 2. Scripted Pipeline

- **Purpose**: Provides flexibility and control over your pipeline using a Groovy-based syntax.
- **Syntax**: Also enclosed within a `pipeline` block.
  
  Example:
  ```groovy
  pipeline {
      // Scripted Pipeline steps here
  }
  ```

### Key Differences

- **Declarative Pipeline**: Structured, easier to read and write, ideal for simpler pipelines with predefined stages.
- **Scripted Pipeline**: More flexible, allows for complex logic and customization, suitable for advanced pipeline requirements.


----
### Fields available in declarative pipeline

In a Declarative Pipeline in Jenkins, you have several key sections and directives that can be used to define and customize your pipeline jobs. Here’s an overview of the available fields and directives:

### Required Sections:
1. **pipeline**: This is the top-level block that defines the entire pipeline.

2. **agent**: Specifies where the pipeline runs, such as a specific Docker image, node, or label.
# Agent Declaration

## Example

The `agent` directive must be defined at the top-level inside the `pipeline` block, but stage-level usage is optional.

```groovy
pipeline {
    agent any
}
```

4. **stages**: This section allows to generate different stages on your pipeline that will be visualized as different segments when the job is run.


 ```groovy
  pipeline {
	agent any
	stages {
		...
	}
}
```

6. **Stage**: Within the `stages` block, individual stages are defined using the `stage` directive.

7. **steps**: Inside each `stage`, the `steps` directive is used to specify the sequence of steps to be executed.
 ```groovy
steps{
sh '
echo "A one line step"
'
sh '''
echo "Multiple lines step"
cd /opt/murali
ls -ltr
pwd
'''
}
```
### Available Directives:
1. **environment**: Defines environment variables scoped either at the pipeline level or within specific stages.

2. **input**: Allows interactive input within a stage, where user input can control the flow of the pipeline.

3. **options**: Specifies various options affecting the entire pipeline or specific stages, such as timeout or retry settings.
 ```groovy
pipeline {
  options {
  
// keep the latest last 10 builds of this pipeline 
buildDiscarder(logRotator(numToKeepStr: '10'))

// Disable the concurrent builds
    disableConcurrentBuilds()

// Add the timestamps to the build logs
    timestamps()
  }
 
}
```
4. **parallel**: Enables parallel execution of multiple stages or steps within a stage.

5. **Parameters**: Allows defining parameters for the pipeline, which can be used to customize pipeline behavior or pass values into the pipeline.

6. **post**: Defines actions or steps to be executed after all stages of the pipeline have completed, such as notifications or cleanup tasks
 ```groovy
   post{

always{
echo ' Congratulations. Successfully run the jenkins job. '
}

}
```

8. **Script**: Executes a block of Scripted Pipeline code within a Declarative Pipeline.

9. **tools**: Specifies tools or tool installations required for the pipeline, such as specific versions of Maven, JDK, or other tools.

 ```groovy
pipeline {

tools{
maven 'Maven-3.8.3' 
jdk 'jdk8'
gardle 'gradle-7.4.2'
}
}
```


10. **Triggers**: Specifies triggers that start the pipeline, such as SCM triggers (e.g., GitHub webhook triggers).Certainly! Here are examples of different trigger configurations in Jenkins Declarative Pipeline:

### Crontab Trigger Example

```groovy
pipeline {
    agent any
    
    triggers {
        cron('H/5 * * * *')  // Job will run every five minutes
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        // Add more stages as needed
    }
}
```

### Poll SCM Trigger Example

```groovy
pipeline {
    agent any
    
    triggers {
        pollSCM('H/5 * * * *')  // Job will run every five minutes if there are SCM changes
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        // Add more stages as needed
    }
}
```

### Upstream Trigger Example

```groovy
pipeline {
    agent any
    
    triggers {
        upstream(upstreamProjects: 'job1, job2', threshold: 'SUCCESS')  // Execute when job1 or job2 are successful
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        // Add more stages as needed
    }
}
```


11. **when**: Defines conditional execution of stages or steps based on predefined conditions, such as success, failure, or specific environment variables.

----

### Build and Push to Nexus using Jenkins  Declarative Pipeline

Your Jenkins Pipeline script defines a basic pipeline that clones a Git repository, builds the code using Maven, and pushes artifacts to Nexus. 

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
        
        stage('Push the artifacts to Nexus') {
            steps {
                // Upload artifact to Nexus repository
                nexusArtifactUploader artifacts: [[artifactId: 'Spring3HibernateApp', file: '/var/lib/jenkins/workspace/jenkins-build-and-deploy/target/Spring3HibernateApp.war', type: 'war']], 
                                     credentialsId: 'Nexus-credentials', 
                                     groupId: 'Spring3HibernateApp', 
                                     nexusUrl: 'http://54.173.248.84:8081', 
                                     nexusVersion: 'nexus3', 
                                     protocol: 'http', 
                                     repository: 'maven-snapshots', 
                                     version: '1.2-SNAPSHOT'
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
  - **Push the artifacts to Nexus:** Uses the Nexus Artifact Uploader plugin (`nexusArtifactUploader`) to upload the built WAR artifact to the Nexus repository.

### Notes:
- Ensure that the credentials (`Github_credentails` and `Nexus-credentials`) are correctly configured in Jenkins Credentials Manager with appropriate permissions.
- Replace placeholders (`/var/lib/jenkins/workspace/jenkins-build-and-deploy/target/Spring3HibernateApp.war`, `http://54.173.248.84:8081`, etc.) with actual paths and URLs relevant to your setup.
- Adjust `groupId`, `artifactId`, `version`, `repository`, and other parameters in `nexusArtifactUploader` according to your project's Maven configuration and Nexus repository setup.
