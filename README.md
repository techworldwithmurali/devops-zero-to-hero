## What is a Shared Library in Jenkins?

- A shared library in Jenkins is a reusable collection of Groovy scripts and supporting files that can be shared among multiple Jenkins pipelines.
- This allows you to centralize commonly used functions, making your Jenkins pipelines more modular, maintainable, and easier to manage.

### Key Benefits:

- **Reusability**: Shared libraries allow you to reuse code across multiple pipelines, reducing duplication and ensuring consistency.
- **Maintainability**: Changes to common functions can be made in one place and automatically propagated to all pipelines that use them.
- **Modularity**: By organizing your code into reusable functions and modules, you can simplify your pipeline scripts and focus on the unique parts of each build.

### Example:

Imagine you have several Jenkins pipelines that need to perform the same tasks with a build tool like Maven. Instead of writing the same Maven code in each pipeline, you can create a shared library that has all the necessary Maven functions. This shared library can then be imported and used in any pipeline, saving time and effort.

## Folder Structure of Jenkins Shared Library

A typical Jenkins shared library follows a specific folder structure to organize the code and resources effectively.

### 1. `src` Directory:

The `src` directory is organized like a typical Java project. This allows you to use the `import` statement to include classes from other parts of the `src` directory.

Example structure:
```
shared-library/
├── src/
│   └── org/
│       └── mycompany/
│           └── MyClass.groovy
```

### 2. `vars` Directory:

The `vars` directory is special because it holds global variables defined in the shared library. These variables can be used in any Jenkins job that imports the shared library.

Example structure:
```
shared-library/
├── vars/
│   ├── gitClone.groovy
│   └── buildCode.groovy
```

### 3. `resources` Directory:

The `resources` directory is a normal directory that can hold any type of file. It's usually used to store static resources needed by the shared library, such as configuration files, templates, or scripts.

Example structure:
```
shared-library/
├── resources/
│   └── mycompany/
│       └── config.yml
```

## Example Usage in a Jenkins Pipeline

Here’s how you can use a shared library in a Jenkins pipeline:

1. **Define the Shared Library in Jenkins Configuration**:
   
   In Jenkins, go to `Manage Jenkins` > `Configure System`, and add the shared library under `Global Pipeline Libraries`.

2. **Use the Shared Library in a Pipeline Script**:

```groovy
  @Library('shared-library') _

pipeline {
    agent any
    tools{
maven 'Maven-3.9.6'
    }

    stages {
        stage('Git clone ') {
            steps {
                gitClone('main', 'github-credentials', 'https://github.com/techworldwithmurali/microservice-one.git')
            }
        }
        stage ('Build the Code'){
            steps{
            buildCode()
            }

        } 
    }
}
```
-----

### Jenkins Pipeline without Shared Library

Without using a Jenkins shared library, you would need to duplicate the common code across multiple Jenkins pipeline scripts. This approach can lead to maintenance challenges and code redundancy. However, you can still organize and reuse code within the same pipeline script by using functions and script blocks.

## Example of a Jenkins Pipeline Script Without Shared Library

Imagine you have several Jenkins pipelines that need to perform the same tasks with a build tool like Maven. Without a shared library, you would need to include the Maven functions directly in each pipeline script.

### Pipeline Script with Common Functions

```groovy
pipeline {
    agent any
   
 tools{
        maven "Maven-3.9.6"
    }
 options {
  timestamps()
  buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '5', numToKeepStr: '2')
  disableConcurrentBuilds()
}
    stages {
        stage('Clone the repo') {
            steps {
              git branch: 'main', changelog: false, credentialsId: 'github-credentials', poll: false, url: 'https://github.com/techworldwithmurali/microservice-one.git'
            }
        }
        
        
         stage('Build the code') {
            steps {
             sh 'mvn clean install'
            }
        }
        
        
    }
}
```

### Explanation:
#### `pipeline { ... }`
The entire script is defined within the `pipeline` block, which is the declarative syntax for defining a Jenkins pipeline.

#### `agent any`
This specifies that the pipeline can run on any available agent.

#### `tools { ... }`
This block defines the tools that are required for the pipeline.
- `maven "Maven-3.9.6"`: Specifies that the pipeline should use Maven version 3.9.6.

#### `options { ... }`
This block sets various options for the pipeline.
- `timestamps()`: Adds timestamps to the console output for better log readability.
- `buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '5', numToKeepStr: '2')`: Configures the log rotation policy. It keeps build logs for up to 5 days and retains the most recent 2 builds.
- `disableConcurrentBuilds()`: Ensures that only one instance of this pipeline can run at a time, preventing concurrent builds.

#### `stages { ... }`
This block defines the different stages of the pipeline.
- **Stage: 'Clone the repo'**
  - **steps { ... }**: The steps to perform in this stage.
  - `git branch: 'main', changelog: false, credentialsId: 'github-credentials', poll: false, url: 'https://github.com/techworldwithmurali/microservice-one.git'`
    - Clones the repository from the specified URL.
    - `branch: 'main'`: Specifies the branch to clone.
    - `changelog: false`: Disables the changelog generation.
    - `credentialsId: 'github-credentials'`: Specifies the credentials to use for accessing the repository.
    - `poll: false`: Disables polling for changes.
- **Stage: 'Build the code'**
  - **steps { ... }**: The steps to perform in this stage.
  - `sh 'mvn clean install'`: Runs the Maven command to clean and build the project.

### Pros and Cons of Not Using Shared Libraries

#### Pros:
- **Simplicity**: Easier to get started without additional configuration.
- **Self-contained Pipelines**: Each pipeline script is self-contained and doesn't depend on external libraries.

#### Cons:
- **Code Duplication**: Common code needs to be copied across multiple pipeline scripts, leading to duplication.
- **Maintenance Overhead**: Updates to common functions need to be made in each pipeline script individually.
- **Inconsistency**: Higher risk of inconsistencies if changes are not propagated to all pipeline scripts.

This Jenkins pipeline script utilizes a shared library to streamline common tasks like cloning a Git repository and building the code. 

-----
### Clone and build the code
### 1. Shared Library Scripts

**gitClone.groovy**
```groovy
def call(String branch, String credentialsId, String url) {
    git branch: branch, credentialsId: credentialsId, url: url
}
```
This function allows you to clone a Git repository using specified branch, credentials, and URL.

**buildCode.groovy**
```groovy
def call() {
    sh 'mvn clean install'
}
```
This function runs the Maven clean install command to build the code.

### 2. Jenkinsfile

```groovy
@Library('shared-library') _

pipeline {
    agent any
    tools {
        maven 'Maven-3.9.6'
    }
    parameters {
        string(name: 'branchName', defaultValue: 'main', description: 'Branch name')
    }
    stages {
        stage('Git clone') {
            steps {
                gitClone(params.branchName, 'github-credentials', 'https://github.com/techworldwithmurali/microservice-one.git')
            }
        }

        stage('Build the Code') {
            steps {
                buildCode()
            }
        }     
    }
}
```
- **@Library('shared-library') _**: This directive imports the shared library named `shared-library`.
- **pipeline**: Defines the Jenkins pipeline.
- **agent any**: Runs the pipeline on any available agent.
- **tools { maven 'Maven-3.9.6' }**: Specifies the Maven tool version to use.
- **parameters { string(name: 'branchName', defaultValue: 'main', description: 'Branch name') }**: Declares a parameter for the branch name, defaulting to 'main'.
- **stages**: Contains the stages of the pipeline.

#### Stages
- **Git clone**: Clones the specified Git repository using the `gitClone` function from the shared library.
- **Build the Code**: Builds the code using the `buildCode` function from the shared library.

