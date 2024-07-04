## What is a Shared Library in Jenkins?

A shared library in Jenkins is a reusable collection of Groovy scripts and supporting files that can be shared among multiple Jenkins pipelines. This allows you to centralize commonly used functions, making your Jenkins pipelines more modular, maintainable, and easier to manage.

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
│   ├── myGlobalVar.groovy
│   └── anotherGlobalVar.groovy
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
   @Library('my-shared-library') _
   
   pipeline {
       agent any
       stages {
           stage('Build') {
               steps {
                   script {
                       // Use a function from the shared library
                       myGlobalVar.mavenBuild()
                   }
               }
           }
       }
   }
   ```
-----
Without using a Jenkins shared library, you would need to duplicate the common code across multiple Jenkins pipeline scripts. This approach can lead to maintenance challenges and code redundancy. However, you can still organize and reuse code within the same pipeline script by using functions and script blocks.

## Example of a Jenkins Pipeline Script Without Shared Library

Imagine you have several Jenkins pipelines that need to perform the same tasks with a build tool like Maven. Without a shared library, you would need to include the Maven functions directly in each pipeline script.

### Pipeline Script with Common Functions

```groovy
pipeline {
    agent any

    environment {
        MAVEN_HOME = tool 'Maven'  // Assuming Maven is configured in Jenkins tools
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    mavenBuild()
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    mavenTest()
                }
            }
        }

        stage('Package') {
            steps {
                script {
                    mavenPackage()
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}

def mavenBuild() {
    echo 'Running Maven Build...'
    sh "${MAVEN_HOME}/bin/mvn clean compile"
}

def mavenTest() {
    echo 'Running Maven Tests...'
    sh "${MAVEN_HOME}/bin/mvn test"
}

def mavenPackage() {
    echo 'Packaging with Maven...'
    sh "${MAVEN_HOME}/bin/mvn package"
}
```

### Explanation:

1. **Define Environment Variables**:
   - `MAVEN_HOME`: Path to the Maven installation.

2. **Pipeline Stages**:
   - `Checkout`: Checks out the source code from the repository.
   - `Build`: Calls the `mavenBuild` function to compile the code.
   - `Test`: Calls the `mavenTest` function to run tests.
   - `Package`: Calls the `mavenPackage` function to package the application.

3. **Common Functions**:
   - `mavenBuild()`: Defines the steps for building the project using Maven.
   - `mavenTest()`: Defines the steps for running tests using Maven.
   - `mavenPackage()`: Defines the steps for packaging the application using Maven.

4. **Post Actions**:
   - `cleanWs()`: Cleans the workspace after the pipeline finishes.

### Pros and Cons of Not Using Shared Libraries

#### Pros:
- **Simplicity**: Easier to get started without additional configuration.
- **Self-contained Pipelines**: Each pipeline script is self-contained and doesn't depend on external libraries.

#### Cons:
- **Code Duplication**: Common code needs to be copied across multiple pipeline scripts, leading to duplication.
- **Maintenance Overhead**: Updates to common functions need to be made in each pipeline script individually.
- **Inconsistency**: Higher risk of inconsistencies if changes are not propagated to all pipeline scripts.
