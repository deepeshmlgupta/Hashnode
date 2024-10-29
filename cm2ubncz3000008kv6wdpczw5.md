---
title: "Jenkins Declarative Pipeline with Docker"
seoTitle: "Building Efficient CI/CD: Jenkins Declarative Pipeline with Docker Int"
seoDescription: "Master Jenkins Declarative Pipeline with Docker to automate CI/CD workflows, enhance deployments, and optimize DevOps processes for scalable builds"
datePublished: Tue Oct 29 2024 10:45:25 GMT+0000 (Coordinated Universal Time)
cuid: cm2ubncz3000008kv6wdpczw5
slug: jenkins-declarative-pipeline
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1730197802065/8dbcd48a-f08a-4aae-8f2e-730c7a475c45.png
tags: docker, devops, jenkins, devops-articles, jenkins-devops, devops-jenkins-docker-integration-cicd, jenkins-on-ubuntu, deepeshmlgupta

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1725947805858/d06ecb04-6350-43de-b1d1-40aee3cc35de.jpeg align="center")

![🚀Day 26: Jenkins Declarative Pipeline with Docker](https://cdn.hashnode.com/res/hashnode/image/upload/v1723800728866/5e81eb75-5357-4de7-9a9a-ab54761f3fbc.png?w=1600&h=840&fit=crop&crop=entropy&auto=compress,format&format=webp align="left")

In today's world of continuous integration and continuous delivery (CI/CD), automation is the backbone of efficient software development. This is where **Jenkins Pipelines** come in handy. They allow teams to automate their processes, from building and testing to deploying their code, all in a streamlined way. So, what exactly is a pipeline, and how does it work in Jenkins? Let's dive in!

### 🛠️ What is a Pipeline?

A **pipeline** in Jenkins is essentially a suite of automated tasks that are executed in a defined sequence. Think of it as a workflow or a set of instructions that tells Jenkins how to build, test, and deploy your application.

Pipelines are typically written in Groovy-based domain-specific language (DSL) and can range from simple scripts with just a few steps to complex workflows that integrate various stages like compilation, testing, deployment, and more.

**Key Benefits of Pipelines**:

* **Automation**: Reduces manual work and human errors.
    
* **Transparency**: Provides visibility into the status of each stage in your process.
    
* **Scalability**: Can handle both simple and complex workflows.
    
* **Version Control**: Pipeline scripts can be versioned just like code, ensuring traceability and easier collaboration.
    

### 🔄 Types of Pipeline: Declarative vs. Scripted Pipeline

In Jenkins, there are two types of pipelines: **Declarative** and **Scripted**. Let’s compare the two:

| **Feature** | **Declarative Pipeline** | **Scripted Pipeline** |
| --- | --- | --- |
| **Syntax** | Simple and more structured | Flexible and powerful, but complex |
| **Error Handling** | Built-in error handling, easier for beginners | Requires custom error handling, more control |
| **Use Case** | Best for most use cases, encourages best practices | Best for complex use cases requiring customization |
| **Complexity** | Easier to write and understand | More complex, especially for large pipelines |
| **Pipeline Block** | Requires `pipeline` block with predefined stages | No strict structure; more freedom |
| **When to Use** | Ideal for standard CI/CD workflows | When you need advanced customizations |

### 📜 What is a Declarative Pipeline?

The **Declarative Pipeline** syntax provides a structured and opinionated way to define your pipeline. It follows a well-defined structure with mandatory sections like `pipeline`, `stages`, and `steps`. This makes it easier to understand and use for most CI/CD workflows.

Here's an example of a simple Declarative Pipeline:

```plaintext
pipeline {
    agent any
    stages {
        stage('Build'){
            steps {
                echo 'Building...'
            }
        }
        stage('Test'){
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}
```

### Task: Create a Declarative Pipeline

* Create a Pipeline to automate the task of creating containers and running them through docker and also Pushing image to Docker Hub, all covered under 1 Script.
    
    **1) Setup Jenkins Environment:** Follow my Blog of Day x for the same.
    
    **2) Create a Pipeline:** Navigate as follows: Dashboard -&gt; New Item -&gt; Select Pipeline -&gt; Give name to Pipeline -&gt; Create -&gt; Give Description -&gt; GitHub Project URL for code cloning.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723799620046/bcb72289-c54e-450c-8d7d-c572096d94c6.jpeg?auto=compress,format&format=webp align="left")
    

**3) Pipeline Script:** Now write the Pipeline Script as below (Select ***Pipeline Script*** for now as option):

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723799691944/fe63ea40-dd0e-4132-b676-277ebd9aaf69.jpeg?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723799707573/d8768569-4d0a-47aa-8914-f1a543b176b6.jpeg?auto=compress,format&format=webp align="left")

* **agent:** Means that we have specified here that it will run on agent which has label dev. ***Note:*** Agent with this label needs to be created.
    
* **stage:** Defines the different stages present in the Pipeline.
    
* **steps:** Defines the steps in order that need to take place in that order.
    
    4. Save the Pipeline.
        
    5. Make sure Agent is ready to run the Job and docker is already installed on it.
        
    6. Play / Run the playbook while monitoring the logs to see if Pipeline ran successfully.
        
    7. Once done, output will look like as shown below and application will be running on Port 8000 as we mapped that in our script.
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723800322596/1e096fdc-8edb-4956-9f62-408445cf484e.jpeg?auto=compress,format&format=webp align="left")
    
* In case we use docker-compose instead of docker, the only change in script is as shown below (***Note: docker-compose should be installed on agent***):
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723800384782/a9061cc3-beba-4669-af01-b50e627ef40a.jpeg?auto=compress,format&format=webp align="left")
    

### 📝 Conclusion

The Jenkins Pipeline is a powerful tool that automates and streamlines your CI/CD processes. By understanding the difference between **Declarative** and **Scripted Pipelines**, you can choose the right approach based on your needs.

* **Declarative Pipelines**: Provide a structured, easier-to-read format and are ideal for most users and workflows.
    
* **Scripted Pipelines**: Offer flexibility and customization for complex use cases, but come with a steeper learning curve.
    

For most teams, the **Declarative Pipeline** is the best starting point, offering simplicity and structure while still being powerful enough to handle a wide range of use cases.

Congrats to you if you try and achieve this successfully, you are one step close to become a successful DevOps Engineer!!!

Happy automating! 🚀