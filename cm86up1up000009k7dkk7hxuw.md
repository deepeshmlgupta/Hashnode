---
title: "Automating ECS Deployment with Bitbucket Pipelines"
seoTitle: "Automate AWS ECS Deployment with Bitbucket Pipelines | Deepesh Gupta"
seoDescription: "Learn how to automate AWS ECS service deployment using Bitbucket Pipelines. This beginner-friendly DevOps guide by Deepesh Gupta covers step-by-step setup."
datePublished: Thu Mar 13 2025 04:30:23 GMT+0000 (Coordinated Universal Time)
cuid: cm86up1up000009k7dkk7hxuw
slug: automating-ecs-deployment
tags: docker, aws, devops, ecs, pipeline, bitbucket-pipelines, deepeshmlgupta, deepeshgupta

---

## **Introduction**

Deploying applications to **AWS ECS (Elastic Container Service)** manually can be time-consuming and error-prone. But with **Bitbucket Pipelines**, we can automate the deployment process, ensuring faster and more reliable updates.

In this blog, I will explain **how to set up a Bitbucket Pipeline to automatically update an ECS service** whenever you push new code to your repository. Even if you're a beginner, don't worry—I’ll explain everything step by step in simple terms.

---

## **Setting Up Environment Variables in Bitbucket**

Instead of hardcoding sensitive information like **AWS credentials**, we use **repository variables**.

### **How to Add Environment Variables in Bitbucket?**

1️⃣ Open your Bitbucket repository.  
2️⃣ Go to **Repository settings** → **Repository variables**.  
3️⃣ Add the following variables:

* **AWS\_KEY\_ID** → Your AWS Access Key
    
* **AWS\_SECRET\_KEY** → Your AWS Secret Access Key
    
* **AWS\_DEFAULT\_REGION** → Your AWS region (e.g., `ap-south-1`)
    
* **CLUSTER\_NAME** → Your ECS Cluster Name
    
* **SERVICE\_NAME** → Your ECS Service Name
    

💡 **Why use environment variables?**

* They **keep credentials secure** and prevent them from being exposed in your pipeline code.
    
* They **allow flexibility**—you can change values without modifying the pipeline.
    

---

## **Understanding the Pipeline Code**

Here’s the complete Bitbucket Pipeline that updates an ECS service whenever new code is pushed to the `prod` branch:

### **Bitbucket-Pipelines.yml**

```plaintext
image: amazon/aws-cli:latest

pipelines:
  branches:
    prod:
      - step:
          name: ECS Service Update
          script:
            # Configure AWS CLI with environment variables
            - aws configure set aws_access_key_id "${AWS_KEY_ID}"
            - aws configure set aws_secret_access_key "${AWS_SECRET_KEY}"
            - aws configure set region "${AWS_DEFAULT_REGION}"

            # Update ECS service with the new image using variables
            - aws ecs update-service --cluster ${CLUSTER_NAME} --service ${SERVICE_NAME} --force-new-deployment 
           
            # Log out from AWS CLI
            - unset AWS_ACCESS_KEY_ID
            - unset AWS_SECRET_ACCESS_KEY
            - unset AWS_DEFAULT_REGION
            - echo "AWS CLI logged out"

          artifacts:
            - build/libs/**

definitions:
  services:
    docker:
      memory: 3072
```

Now, let’s break this down so you can understand **what each part does**.

---

## **Step-by-Step Explanation of the Pipeline**

### **1\. Selecting the AWS CLI Image**

```plaintext
image: amazon/aws-cli:latest
```

* This tells Bitbucket to use the official **AWS CLI Docker image**.
    
* The AWS CLI is needed to **interact with AWS ECS** and update the service.
    

---

### **2\. Defining the Branch for Deployment**

```plaintext
pipelines:
  branches:
    prod:
```

* This pipeline will only run when **code is pushed to the** `prod` branch.
    
* You can change `prod` to any other branch (e.g., `main`, `staging`) depending on your workflow.
    

---

### **3\. Running Deployment Steps**

```plaintext
      - step:
          name: ECS Service Update
          script:
```

* This defines a **step** named "ECS Service Update" that contains the deployment process.
    

---

### **4\. Configuring AWS CLI**

```plaintext
            - aws configure set aws_access_key_id "${AWS_KEY_ID}"
            - aws configure set aws_secret_access_key "${AWS_SECRET_KEY}"
            - aws configure set region "${AWS_DEFAULT_REGION}"
```

* The AWS CLI requires authentication to access **AWS ECS**.
    
* Instead of **hardcoding sensitive credentials**, we use **environment variables** stored securely in **Bitbucket repository variables** (more on this later).
    

---

### **5\. Updating the ECS Service**

```plaintext
          - aws ecs update-service --cluster ${CLUSTER_NAME} --service ${SERVICE_NAME} --force-new-deployment
```

* This command tells AWS to update the **ECS service** with the latest image and configuration.
    
* `${CLUSTER_NAME}` and `${SERVICE_NAME}` are variables representing:
    
    * **CLUSTER\_NAME** → The name of your ECS cluster
        
    * **SERVICE\_NAME** → The name of the ECS service to be updated
        

💡 **What does** `--force-new-deployment` do?

* It forces the ECS service to **redeploy the running tasks** with the latest configuration, even if no changes are detected.
    

---

### **6\. Logging Out from AWS CLI**

```plaintext
            - unset AWS_ACCESS_KEY_ID
            - unset AWS_SECRET_ACCESS_KEY
            - unset AWS_DEFAULT_REGION
            - echo "AWS CLI logged out"
```

* After the deployment, we **clear the credentials** to ensure security.
    

---

### **7\. Storing Build Artifacts (Optional)**

```plaintext
         artifacts:
            - build/libs/**
```

* If your pipeline builds files (like a `.jar` file for Java applications), they will be stored as **artifacts**.
    
* These artifacts can be used in later pipeline steps.
    

---

### **8\. Defining Docker Memory Usage**

```plaintext
definitions:
  services:
    docker:
      memory: 3072
```

* **Docker** is required for some ECS tasks, so we allocate **3072 MB (3GB) of memory** for it.
    
* If you face memory issues, you can increase or decrease this value.
    

---

## **How the Pipeline Works in Action**

1️⃣ You push your code to the `prod` branch.  
2️⃣ **Bitbucket Pipelines automatically starts the deployment.**  
3️⃣ The pipeline:

* **Authenticates with AWS** using stored credentials.
    
* **Updates the ECS service**, triggering a new deployment.
    
* **Logs out securely** after the deployment.  
    4️⃣ Your latest code is now running on **AWS ECS**! 🚀
    

---

## **Benefits of This Pipeline**

✅ **Fully Automated Deployment** – No manual intervention needed.  
✅ **Secure Authentication** – Uses **Bitbucket repository variables** to store AWS credentials.  
✅ **Works with Any ECS Service** – Just update the **CLUSTER\_NAME** and **SERVICE\_NAME**.  
✅ **Beginner-Friendly** – Simple steps that even a DevOps newbie can follow.

---

## **Conclusion**

Setting up a **Bitbucket Pipeline** for **ECS deployment** allows you to automate the entire process of updating your application. With just a `git push`, you can deploy new versions of your service in minutes!

If you're looking to scale your **DevOps automation** further, consider integrating **Terraform for infrastructure as code** or using **Ansible for configuration management**.

Let me know in the comments if you have any questions! 🚀