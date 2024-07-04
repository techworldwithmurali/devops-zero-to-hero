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
