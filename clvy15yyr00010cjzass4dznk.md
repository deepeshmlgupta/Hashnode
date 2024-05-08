---
title: "How to install Tools in Linux Operating System"
datePublished: Wed May 08 2024 16:25:06 GMT+0000 (Coordinated Universal Time)
cuid: clvy15yyr00010cjzass4dznk
slug: how-to-install-tools-in-linux-operating-system
tags: java, devops, jenkins, linux-for-beginners, deepeshmlgupta

---

## **How to install docker on Ubuntu**

To, install docker on Ubuntu, just run the following commands,

1. Update your system,
    

```plaintext
sudo apt-get update -y
```

1. Install docker,
    

```plaintext
sudo apt-get install docker.io -y
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689929244067/eba2a0a6-f9f5-49b0-ac2f-ad079fb747d9.png?auto=compress,format&format=webp align="left")

1. Start docker,
    

```plaintext
sudo systemctl start docker
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689929330033/7ea6695d-3722-4a47-87a8-614fb97d9055.png?auto=compress,format&format=webp align="left")

Now, you have successfully installed docker on Ubuntu

Let's check how to install Jenkins on Ubuntu

## How to install Jenkins on Ubuntu

1. Update your Ubuntu Server,
    

```plaintext
sudo apt update -y
```

1. Install Java on your Ubuntu server, because Jenkins uses java in the backend, so java is the pre-requisite for Jenkins installation.
    

```plaintext
sudo apt install openjdk-11-jre -y
```

Check java version,

```plaintext
sudo java -version
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689929662035/501aea8f-b5d2-428a-85a6-c0066f6569e8.png?auto=compress,format&format=webp align="left")

Now, add Jenkins key,

```plaintext
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
```

Now, again update your system,

```plaintext
sudo apt-get update -y
```

Install Jenkins,

```plaintext
sudo apt-get install jenkins -y
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689931436463/ece5a599-366f-452e-82c4-107458144710.png?auto=compress,format&format=webp align="left")

Go to security groups of the server and add inbound rule for port 8080 and If you see the below page on port 8080, then you have successfully installed jenkins on ubuntu.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689931547437/b1d74c60-0834-4daa-9b5e-7b764de73c35.png?auto=compress,format&format=webp align="left")