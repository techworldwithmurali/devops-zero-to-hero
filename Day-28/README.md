### Jenkins Shared Library - Build the Docker image and Push to AWS ECR

![Dockerizing and Pushing to AWS ECR - Tech World with Murali - Moole Muralidhara Reddy.png](https://github.com/techworldwithmurali/devops-zero-to-hero/blob/main/Day-28/images/Day%20%2027-%20%20Dockerizing%20and%20Pushing%20to%20AWS%20ECR%20-%20Moole%20Muralidhara%20Reddy%20-%20Tech%20World%20with%20Murali.png)


### Shared Library Scripts

**gitClone.groovy**
```groovy
def call(String branch, String credentialsId, String url) {
    git branch: branch, credentialsId: credentialsId, url: url
}
```

**buildCode.groovy**
```groovy
def call() {
    sh 'mvn clean install'
}
```

**dockerBuild.groovy**
```groovy
def call(String aws_account_id, String region, String ecrRepoName) {
    sh """
        docker build -t ${ecrRepoName}:${BUILD_NUMBER} .
        docker tag ${ecrRepoName}:${BUILD_NUMBER} ${aws_account_id}.dkr.ecr.${region}.amazonaws.com/${ecrRepoName}:${BUILD_NUMBER}
    """
}
```

**dockerImagePush.groovy**
```groovy
def call(String aws_account_id, String region, String ecrRepoName) {
    sh """
        aws ecr get-login-password --region ${region} | docker login --username AWS --password-stdin ${aws_account_id}.dkr.ecr.${region}.amazonaws.com
        docker push ${aws_account_id}.dkr.ecr.${region}.amazonaws.com/${ecrRepoName}:${BUILD_NUMBER}
    """
}
```

### Jenkinsfile

```groovy
@Library('shared-library') _

pipeline {
    agent any
    tools {
        maven 'Maven-3.9.6'
    }
    
    parameters {
        string(name: 'branchName', defaultValue: 'main', description: 'Branch name')
        string(name: 'ecrRepoName', defaultValue: 'microservice-one', description: 'ECR Repository Name')
        string(name: 'accountNumber', defaultValue: '590184088314', description: 'AWS Account Number')
        choice(name: 'region', choices: ['us-east-1','us-west-2'], description: 'Select AWS region')
    }
    
    stages {
        stage('Clone the Repo') {
            steps {
                script {
                    gitClone(params.branchName, 'github-credentials', 'https://github.com/telugudevopsguru/microservice-one.git')
                }
            }
        }
        stage('Build Code') {
            steps {
                buildCode()
            }
        }
        
        stage('Build and Tag Docker Image') {
            steps {
                script {
                    dockerBuild(params.accountNumber, params.region, params.ecrRepoName)
                }
            }
        }
       
        stage('Push to ECR') {
            steps {
                script {
                    dockerImagePush(params.accountNumber, params.region, params.ecrRepoName)
                }
            }
        } 
    }
}
```

### Explanation

- **Shared Library Scripts**: 
  - `gitClone.groovy`: Clones the Git repository.
  - `buildCode.groovy`: Builds the code using Maven.
  - `dockerBuild.groovy`: Builds and tags the Docker image.
  - `dockerImagePush.groovy`: Pushes the Docker image to Amazon ECR.

- **Jenkinsfile**:
  - **@Library('shared-library') _**: Imports the shared library.
  - **pipeline**: Defines the Jenkins pipeline.
  - **agent any**: Specifies that the pipeline can run on any available agent.
  - **tools**: Defines Maven tool configuration.
  - **parameters**: Defines parameters for the pipeline.
  - **stages**: Contains the different stages of the pipeline:
    - **Clone the Repo**: Clones the specified Git repository.
    - **Build Code**: Builds the project using Maven.
    - **Build and Tag Docker Image**: Builds and tags the Docker image using the shared library script.
    - **Push to ECR**: Pushes the Docker image to Amazon ECR using the shared library script.
