---
title: "Docker Interview Questions"
seoTitle: "Interview Docker"
seoDescription: "Interview Question by Deepesh Gupta"
datePublished: Tue Oct 15 2024 15:10:53 GMT+0000 (Coordinated Universal Time)
cuid: cm2akytru000809l7gv0phixs
slug: docker-interview-questions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1729000532303/7c2c9ce9-9c89-475b-a98f-3050adeb5b99.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1729003708228/fb4a2958-0979-44c6-9015-25c8955406c8.png
tags: docker, devops, docker-interview-questions, deepeshmlgupta

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1725947699531/d5ba59ba-34db-4c3e-91da-e0ae023a895a.jpeg align="center")

## **Finally!! 🎉**

You have completed ✅ the Docker hands-on sessions, and I hope you have learned something valuable from it. 🙌

Docker being a crucial topic for DevOps Engineer interviews, especially for freshers. Here are some essential questions to help you prepare and ace your Docker interviews:

1. **Difference between an Image, Container, and Engine:**
    
    * **Image:** A read-only template with instructions to create a Docker container.
        
    * **Container:** A running instance of a Docker image.
        
    * **Engine:** The runtime that manages containers on a host system.
        
2. **Difference between the Docker command COPY vs ADD:**
    
    * **COPY:** Copies files/directories to the container without any additional functionality.
        
    * **ADD:** Similar to COPY but also supports fetching remote URLs and extracting archives.
        
3. **Difference between the Docker command CMD vs RUN:**
    
    * **CMD:** Sets the default command to run when the container starts.
        
    * **RUN:** Executes a command during the build process and creates a layer in the image.
        
4. **How will you reduce the size of a Docker image?**
    
    * Use multi-stage builds, minimize the number of layers, remove unnecessary files, and use `.dockerignore`.
        
5. **Why and when to use Docker?**
    
    * Use Docker for consistent environments, easy deployment, scalability, and isolation of applications for their easy shipment.
        
6. **Explain the Docker components and how they interact with each other.**
    
    * Components: Docker Engine, Docker Images, Docker Containers, Docker Daemon, Docker CLI, and Docker Compose.
        
    * Interaction: The Engine runs containers from images, managed by the Daemon, controlled via the CLI, and orchestrated by Compose.
        
7. **Explain the terminology: Docker Compose, Dockerfile, Docker Image, Docker Container.**
    
    * **Docker Compose:** Tool for defining and running multi-container Docker applications.
        
    * **Dockerfile:** Script with instructions to build a Docker image.
        
    * **Docker Image:** A template for creating Docker containers.
        
    * **Docker Container:** An isolated environment to run applications.
        
8. **In what real scenarios have you used Docker?**
    
    * Deploying microservices, CI/CD pipelines, isolating development environments, and running legacy applications.
        
9. **Docker vs Hypervisor?**
    
    * **Docker:** Lightweight containers sharing the host OS kernel.
        
    * **Hypervisor:** Virtual machines with full OS, more resource-intensive.
        
10. **Advantages and disadvantages of Docker?**
    
    * **Advantages:** Portability, efficiency, scalability, and faster deployment.
        
    * **Disadvantages:** Security concerns, networking complexity, and data persistence issues.
        
11. **What is a Docker namespace?**
    
    * A feature for isolating resources (e.g., PID, network) in containers.
        
12. **What is a Docker registry?**
    
    * A storage and distribution system for Docker images (e.g., Docker Hub).
        
13. **What is an entry point?**
    
    * The command that runs as the main process inside a container.
        
14. **How to implement CI/CD in Docker?**
    
    * Use Docker to build, test, and deploy containers in automated CI/CD pipelines.
        
15. **Will data on the container be lost when the Docker container exits?**
    
    * Yes, data is lost when a container exits unless volumes or bind mounts are used to backup the container data.
        
16. **What is a Docker swarm?**
    
    * A native clustering and orchestration tool for Docker containers.
        
17. **What are docker commands for the following:**
    
    * **Viewing running containers:** `docker ps`
        
    * **Running a container under a specific name:** `docker run --name <name> <image>`
        
    * **Exporting a Docker image:** `docker save -o <file> <image>`
        
    * **Importing an existing Docker image:** `docker load -i <file>`
        
    * **Deleting a container:** `docker rm <container_id>`
        
    * **Removing all stopped containers, unused networks, build caches, and dangling images:** `docker system prune`
        
18. **What are the common Docker practices to reduce the size of Docker images?**
    
    * Multi-stage builds, using smaller base images, minimizing layers, and cleaning up after package installations.
        
19. **How do you troubleshoot a Docker container that is not starting?**
    
    * Check logs with `docker logs <container_id>`, inspect with `docker inspect`, and verify configuration files.
        
20. **Docker networking model:**
    
    * Docker uses bridge, overlay, host, and macvlan networks to connect containers.
        
21. **How do you manage persistent storage in Docker?**
    
    * Use Docker volumes or bind mounts to persist data outside the container lifecycle.
        
22. **How do you secure a Docker container?**
    
    * Limit privileges, use secure base images, scan images for vulnerabilities, and use Docker security features like seccomp and AppArmor.
        
23. **What is docker overlay networking:**
    
    * A network that allows containers across different hosts to communicate securely in a Docker Swarm.
        
24. **How do you handle environment variables in Docker?**
    
    * Pass environment variables using `-e` or `--env-file` options when running containers.
        

I hope these questions will surely help you ace your next interview for Docker. Happy learning! 😊