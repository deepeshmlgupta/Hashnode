---
title: "Setting Up Jenkins & Creating Your First Pipeline😃"
seoTitle: "How to Set Up Jenkins and Create Your First Pipeline | Step-by-Step Gu"
seoDescription: "Learn how to set up Jenkins and create your first pipeline in this comprehensive guide by Deepesh Gupta. Enhance your DevOps skills and automate your CI/CD"
datePublished: Tue Oct 15 2024 17:23:06 GMT+0000 (Coordinated Universal Time)
cuid: cm2apouhr000408mm5vohd10e
slug: jenkins-installation
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1729013045498/b9decc8a-370f-4271-a941-bd9bcdd70ba2.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1729012790515/11519552-cd4a-4341-b1b5-d740a5d2a397.png
tags: devops, jenkins, jenkins-devops, devops-journey, jenkins-installation, devopscommunity, deepeshmlgupta

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1725947729857/a5dfbcc8-6059-4773-bcfc-ba68b256a6d8.jpeg align="center")

![Day 24: Setting Up Jenkins & Creating Your First Pipeline😃](https://cdn.hashnode.com/res/hashnode/image/upload/v1723654154051/eebdce13-1fdf-4f6f-b320-752760ffe2f9.png?w=1600&h=840&fit=crop&crop=entropy&auto=compress,format&format=webp align="left")

Today, we’ll be focusing on installing and configuring Jenkins on our systems. Additionally, we’ll take on an exciting challenge—creating a freestyle pipeline to apply what we've learned. Ready to enhance your automation skills? Let’s get started! 💻🔧

### **Setting Up Jenkins**

**Prerequisites:**

* Minimum hardware requirements:
    
    * 256 MB of RAM
        
    * 1 GB of drive space (10 GB recommended if running Jenkins as a Docker container)
        
* Java 11 or 17 is required.
    

**Installing Jenkins:**

1. **Update the Packages:**
    
    ```plaintext
      sudo apt-get update
    ```
    
2. **Install Java:**
    
    ```plaintext
      sudo apt install openjdk-11-jre
    ```
    
3. **Check Java Installation successful or not:**
    
    ```plaintext
      java --version
    ```
    
4. **Add Jenkins Repository Key:**
    
    ```plaintext
      curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
    ```
    
5. **Add Jenkins Repository:**
    
    ```plaintext
      echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
    ```
    
6. **Update Package Lists and Install Jenkins:**
    
    ```plaintext
      sudo apt-get update
      sudo apt-get install jenkins
    ```
    
7. **Start Jenkins:**
    
    ```plaintext
      sudo systemctl start jenkins
    ```
    
8. **Check Jenkins Status:**
    
    ```plaintext
      systemctl status jenkins
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723654569766/b37738c0-2cf9-48bb-a8a4-ef32ca3111ff.jpeg?auto=compress,format&format=webp align="left")
    
9. **Open Port 8080 on your EC2 Instance:** Since Jenkins by default runs on port 8080 thus we are allowing this port the permission.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723654635680/1f7479a8-5089-4617-99cc-38b0e4eb236b.jpeg?auto=compress,format&format=webp align="left")
    
10. **Access Jenkins Web Interface:** Open a web browser and enter the public IP address of your EC2 instance followed by `:8080`(e.g.,`http://<your_public_ip>:8080`).
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723654761773/b8a8a826-c02a-4bad-80d1-f76673dea186.jpeg?auto=compress,format&format=webp align="left")
    
    To retrieve the Jenkins initial admin password, enter the following commands in your Linux terminal:
    
    <div data-node-type="callout">
    <div data-node-type="callout-emoji">💡</div>
    <div data-node-type="callout-text">/var/lib/jenkins/secrets/initialAdminPassword</div>
    </div>
    
    Then, run:
    
    ```plaintext
    sudo cat /var/lib/jenkins/secrets/initialAdminPassword
    ```
    
    This will generate the admin password required for your first login.
    
11. **Find Admin Password:** Go to the specified Path on your EC2 instance as mentioned above to get Administrator Password.
    

**Customize Jenkins:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723654831715/b71bded3-b64a-420f-a25e-4027efe72f54.jpeg?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723654944892/76028c0e-d2dc-4efd-a45e-d18b50a25495.jpeg?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723654968513/166a0897-6cba-43f9-b310-db82aa9ca17c.jpeg?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723654997575/5b2d59b6-fe1e-4576-8baa-19715e2504f6.jpeg?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723655017514/532aead6-0df4-4247-9b06-02063ffc7ced.jpeg?auto=compress,format&format=webp align="left")

Congratulations, your setup is ready and we are ready to use it.

## Task: Create a Freestyle Pipeline to Print "Hello World"

1. Go to New Item on Dashboard on top left.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723655129216/ca0949ee-98eb-41eb-bb30-7bf57fca602e.jpeg?auto=compress,format&format=webp align="left")
    
2. Enter Item name and select on Freestyle Project and click ok.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723655166656/72fe4c2a-e361-4d93-80fe-b97f489ce65e.jpeg?auto=compress,format&format=webp align="left")
    
3. Give a description about what your project is about for others to understand easily.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723655224188/06773d71-080d-497e-bff1-68b3c9df8b35.jpeg?auto=compress,format&format=webp align="left")
    
4. Select **"Execute Shell"** in Build Steps.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723655268303/7bbb3582-8b9a-4f79-85a7-6d4dd72be58f.jpeg?auto=compress,format&format=webp align="left")
    
5. Give the required steps to execute. Since here we only want to print Hello World thus we have only 1 command which is echo command.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723655286901/69bea9b0-4bd9-4be9-b42d-b1ee7fe84da6.jpeg?auto=compress,format&format=webp align="left")
    
6. Click on **Build Now** on left to start.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723655317336/65f546c3-9081-4096-a32f-b722cd6eaac5.jpeg?auto=compress,format&format=webp align="left")
    
7. The green tick shows that the project ran successfully.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723655334232/dced5a5f-ea91-462f-9bf4-04622b7d11d6.jpeg?auto=compress,format&format=webp align="left")
    

Console output shows what was the output and thus verifies the success. We finally see the output "Hello World" which we wanted.

## Conclusion

In conclusion, Jenkins stands as a cornerstone of modern DevOps practices, providing a robust platform to automate the entire software delivery process. With its powerful pipeline features and extensive plugin ecosystem, Jenkins significantly improves the efficiency and reliability of CI/CD workflows. As emphasized by Deepesh Gupta, embracing Jenkins can elevate your automation skills to new heights! 🚀