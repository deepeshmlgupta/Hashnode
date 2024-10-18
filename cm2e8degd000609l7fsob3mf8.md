---
title: "Jenkins Freestyle Project for DevOps Engineers"
datePublished: Fri Oct 18 2024 04:29:23 GMT+0000 (Coordinated Universal Time)
cuid: cm2e8degd000609l7fsob3mf8
slug: jenkins-freestyle-project
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1729225456177/d3fd746a-cf43-4733-bf86-9f12438654f2.png
tags: docker, devops, jenkins, jenkins-devops, jenkins-pipeline, deepeshmlgupta

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1725947791261/d6734411-edb8-4712-8937-36ef026bc6d1.jpeg align="center")

![Day 25: Jenkins Freestyle Project for DevOps Engineers](https://cdn.hashnode.com/res/hashnode/image/upload/v1723798504766/f3177df5-bfc1-4498-9c22-c6e820a0297d.png?w=1600&h=840&fit=crop&crop=entropy&auto=compress,format&format=webp align="left")

### **Understanding a Build Job?**

A Jenkins build job defines the configuration required to automate specific tasks within the application build process. These tasks typically include:

* Gathering dependencies
    
* Compiling and archiving code
    
* Transforming source code
    
* Running tests
    
* Deploying to various environments
    

Jenkins provides multiple types of build jobs, such as:

* Freestyle projects
    
* Pipelines
    
* Multi-configuration projects
    
* Folders
    
* Multibranch pipelines
    
* Organization folders
    

### What is a Freestyle Project? 🤔

A freestyle project in Jenkins is a flexible option for building, testing, and deploying software. It allows for different configurations and steps to be executed. Here's an example of what you can achieve with a freestyle project.

### Tasks:

#### **Task1: Creating Jenkins Freestyle Project**

* **Set up an agent**: Make sure to configure an agent where your job will run.
    
* **Create a new freestyle project**:
    
    * From the Jenkins Dashboard, navigate to:  
        **New Item** → **Freestyle Project** → Enter a project name → **Create**.
        
* **Configure the build step**:
    
    * Scroll to the "Build" section.
        
    * Choose the **Execute Shell** option.
        
    * Enter the following commands to build and run a Docker container:
        
        ```plaintext
        cd /home/ubuntu/django-notes-app  # Path where the project is cloned
        docker build -t my-app .
        docker run -d -p 8080:8080 my-app
        ```
        

* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723797319415/8618f873-5531-4ef5-a940-cd41e85da710.jpeg?auto=compress,format&format=webp align="left")
    
* As seen below we have the Console Output and Stage output (Build no. 11) which shows that our project ran successfully.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723797480696/1b5a99d0-c274-48b7-9c24-11f16ad7b0db.jpeg?auto=compress,format&format=webp align="left")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723797554187/88b0b29e-f422-4906-a5a9-c3fd12e4f5d5.jpeg?auto=compress,format&format=webp align="left")
    
* Application is also running fine on the port mentioned. To access the application type the following in browser: **https://&lt;host-ip&gt;:&lt;port-number&gt;**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723797631197/1a400962-605f-4b42-8330-50d4962f0a26.jpeg?auto=compress,format&format=webp align="left")
    
    #### **Task2: Running Docker Compose**
    
    1. Ensure that docker compose is installed on the agent on which the job will run.
        
    2. **Create Jenkins Project for Docker Compose**:
        
        * We have already created a Freestyle Project as above.
            
        * Click on that Project -&gt; Configure and in Build section -&gt; Execute shell commands make the below changes.
            
    3. **Run** `docker-compose down` and `docker-compose up -d` Command:
        
        ```plaintext
         << comment
         We run this command first as due to above TASK1 build, container
         will already be running so we need to stop that first and then run 
         again to test docker compose. Note: Make sure to remove docker run
         command from execute shell written before, before writing compose commands.
         comment 
        
         docker-compose -f path/to/your/docker-compose.yml down
         docker-compose -f path/to/your/docker-compose.yml up -d
        ```
        
        ## Conclusion
        
        Today was Day of DevOps, where we deep dived about what is a freestyle project and a build job and also did a small task to have practical hands on and be confident in it. I hope I was able to help you and guide you in this. For any queries please feel to reach me out on Linkedin.
        
        Happy Learning, Happy growth!!