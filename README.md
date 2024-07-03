### What is Jenkins Pipeline?

Jenkins Pipeline is a suite of plugins that allows you to implement and integrate continuous delivery pipelines into Jenkins. It provides an extensible automation server for creating simple or complex delivery pipelines "as code" using a Domain-specific Language (DSL).

### Jenkinsfile

A Jenkinsfile is a text file that defines the pipeline workflow as code. It allows you to automate the building, testing, and deployment of your software projects.

### Benefits of Using Jenkinsfile

- **Automated Pipelines**: Define pipelines for all branches and execute pull requests with a single Jenkinsfile.
- **Code Review**: Review and version control your pipeline configurations.
- **Auditability**: Track changes and audit your pipeline configurations over time.
- **Collaboration**: Multiple users can modify and contribute to the Jenkinsfile.
- **Source of Truth**: Jenkinsfile serves as the single source of truth for your pipeline configuration.

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

Both types of syntax enable you to define continuous integration and delivery workflows in Jenkins, tailored to your project's specific needs and complexity.

----
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

6. **post**: Defines actions or steps to be executed after all stages of the pipeline have completed, such as notifications or cleanup tasks.

7. **Script**: Executes a block of Scripted Pipeline code within a Declarative Pipeline.

8. **tools**: Specifies tools or tool installations required for the pipeline, such as specific versions of Maven, JDK, or other tools.

9. **Triggers**: Specifies triggers that start the pipeline, such as SCM triggers (e.g., GitHub webhook triggers).

10. **when**: Defines conditional execution of stages or steps based on predefined conditions, such as success, failure, or specific environment variables.

