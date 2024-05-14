---
title: "Docker Commands"
datePublished: Tue May 14 2024 18:30:42 GMT+0000 (Coordinated Universal Time)
cuid: clw6qalnx00050aigahsmeqlq
slug: docker-commands
tags: docker, devops, docker-images, docker-command, deepeshmlgupta

---

### **Docker run command**

The docker run command is used to run the Docker container using Docker images.

> ***Example:***

```plaintext
docker run hello-world
```

---

### Docker inspect command

docker inspect command gives us all the details about the docker container.

In simple terms, the docker inspect command provides all the details of a container.

let's see it with an example,

```plaintext
docker inspect <containerID>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692348472162/1b9d1649-d4d0-4bd4-a788-4229c3219cf0.png?auto=compress,format&format=webp align="left")

Here, after hitting the docker inspect command we got lots of container details like

* Container ID
    
* Container Created Time
    
* Path
    
* State ( Status, running, paused )
    

and many more.

---

### Docker port command

docker port command lists all the port mappings for a container.

> ***Example:***

```plaintext
docker port <containerID>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692348846941/229ad4b5-9e2e-4542-892d-5de363c2f831.png?auto=compress,format&format=webp align="left")

---

### Docker stats command

docker stats command is used to check the statistics of one or more docker containers like CPU, Memory Usage, PID etc.

> ***Example:***

```plaintext
docker stats <containerID>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692349035788/a6a1fbf2-ad1f-4d74-a9c7-fc91603492b1.png?auto=compress,format&format=webp align="left")

---

### Docker top command

The docker top command is used to list all the processes running inside the container.

> ***Example:***

```plaintext
top <ContainerID>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692349228587/8a144dfb-adf4-4333-a4dd-22c6c5289bb8.png?auto=compress,format&format=webp align="left")

As we can see, I am running python inside the docker container, so it is showing python3.

---

### Docker save command

The docker save command is used to save docker image to tar archive file

> ***Example:***

```plaintext
docker save -o <tarfilename>.tar <dockerimagename>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692349864648/109c42e2-0c4f-4eb7-9650-401c50bbf269.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692349904178/301dbc3e-a466-4b68-a413-93a42eefa33b.png?auto=compress,format&format=webp align="left")

Here, the python:3.6.0.tar file is created using the docker save command

---

### Docker load command

The docker load command is used to load docker image from tar archive file which was created using docker save command.

> ***Example:***

```plaintext
docker load -i <tarfilename>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692350242847/c246236d-c56e-4979-8afe-c58d6ab834f4.png?auto=compress,format&format=webp align="left")

In the above screenshot, we have loaded python3.6 image from tar archive file using docker load command