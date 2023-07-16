---
title: "Getting more into Docker"
datePublished: Sun Jul 02 2023 12:53:00 GMT+0000 (Coordinated Universal Time)
cuid: cljlfn9vq00010amj4mu57a39
slug: getting-more-into-docker
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688302859515/aa235013-ea26-4522-9cdf-b26dbd737ce7.png
tags: linux, docker, devops, dockerfile, docker-images

---

# **What are containers?**

Containers are a way to package software in a format that can run consistently across different environments.

![](https://miro.medium.com/v2/resize:fit:494/1*HJJQKENaPTKr12mxT0q5Xg.png align="left")

This makes it easier to develop, test, and deploy applications, because it eliminates the need to worry about differences in libraries or system configurations on different machines.

Containers allow you to package an application with all of its dependencies, and ship it as a single unit.

This makes it easier to move the containerized application between different computing environments, such as from a developer’s laptop to a staging or production environment.

# **What is virtual machine (VM)?**

A virtual machine (VM) is a software implementation of a physical computer that executes programs like a real machine. VMs provide a way to run multiple operating systems on a single physical computer, each with its own virtual environment and resources.

In a virtualized environment, the host machine runs a hypervisor, which is a software layer that allows multiple VMs to share the resources of the physical host. Each VM runs its own OS, and applications running inside a VM are isolated from the host and from other VMs.

This allows you to run multiple different OSes on the same physical machine, and to run applications that are incompatible with the host OS.

**You can launch multiple images at same time and it will not occupy more space is the benefit of docker(containers) over virtual machine.**

# **Docker image VS Docker container**

A Docker image is a lightweight, stand-alone, executable package that includes everything needed to run a piece of software, including the application code, libraries, dependencies, and runtime.

Images are created using the `docker build` command and are stored in a Docker registry, such as Docker Hub.

![](https://miro.medium.com/v2/resize:fit:700/1*ge46z2N5se-vCmfdWtHR_w.png align="left")

A Docker container is a running instance of a Docker image. You can create a container from an image using the `docker run (image name)`command. When you start a container, Docker creates a new runtime environment, which includes a copy of the files in the image, and runs the application inside the container.

You can create multiple containers from the same image, and they will all contain the same application code and dependencies. Each container is an isolated environment, and the applications running in different containers do not interfere with each other.

This makes it easy to scale up or down the number of containers running an application, depending on demand.

Docker image is a template for creating containers, and a Docker container is a running instance of a Docker image.

# **What is Docker Hub?**

Docker Hub is a cloud-based repository in which Docker users and partners create, test, store and distribute container images.

We can use Docker Hub to find pre-built images that you can use as the basis for your own containerized applications, or you can use it to build, test, and store your own custom images.

It is a great resource for quickly and easily deploying containerized applications.

**Docker Hub is basically a cloud-hosted version of Docker Registry.**

**To push an image to Docker Hub :**

1. Log into Docker Cloud with the **\# docker login** command.
    
2. Tag the specified image using **\# docker tag** command**.**
    
3. Push the image to Docker Hub with **\# docker push.**
    
4. Check Docker Cloud to ensure the image appears in her repository.
    
5. A user can pull an image from Docker Hub with the **\# docker pull** command.
    

# **What is Dockerfile?**

A Dockerfile is a text file that contains instructions for how to build a Docker image.

It is used to automate the process of building a Docker image, so that you don’t have to manually specify all the steps required to build the image.

A Dockerfile consists of a series of commands, each of which specifies a step in the process of building the image.

These commands can be used to specify things like the base image to use, the packages to install, the commands to run, and so on.

# **Most commonly used tags in a Dockerfile:**

* `FROM`: Specifies the base image to use for the image being built.
    
* `RUN`: Executes a command during the build process.
    
* `CMD`: Specifies the default command to run when the container is started.
    
* `ENV`: Sets an environment variable in the container.
    
* `COPY`: Copies files or directories from the host file system into the container.
    
* `EXPOSE`: Exposes a specific port or ports to be used by the container.
    
* `LABEL`: Adds metadata to the image in the form of key-value pairs.
    
* `USER`: Specifies the user to use when running the container.
    
* `WORKDIR`: Sets the working directory for the container.
    

# **Here is an example of a simple Dockerfile:**

![](https://miro.medium.com/v2/resize:fit:579/1*t4lcVWq34LBKSJ9EI-vB8w.png align="left")

This Dockerfile specifies that it will use the `node:18-alpine` image as the base image. Working directory will be /app .

And it will copy all the files at the current location in the container.

RUN **yarn install** is used to **install** all dependencies for a project.

It sets the default command for the container to `node src/index.js`.

To build an image from a Dockerfile, you can use the `#docker build` command.

![](https://miro.medium.com/v2/resize:fit:595/1*FPxqe2FTG98G3AgEXHhkEw.png align="left")

This will build an image from the Dockerfile in the current directory and give it the name `my_image`.

To run this image use the `#docker run` command.

![](https://miro.medium.com/v2/resize:fit:587/1*6zKFb0-J19ewN_6_e_Bgig.png align="left")

This command will run the `my_image` container, mapping port 80 on the host to port 80 in the container.

## List of Commands.

1. Working with Images:
    

a. `docker search <term>`: Search for Docker images available on Docker Hub. Example: `docker search nginx`

b. `docker pull <image>:<tag>`: Download a specific image from a registry. Example: `docker pull ubuntu:latest`

c. `docker image ls`: List all available images on your system.

1. Managing Containers:
    

a. `docker ps`: List all running containers.

b. `docker ps -a`: List all containers (including stopped ones).

c. `docker run <image> <command>`: Run a command in a new container. Example: `docker run ubuntu echo "Hello, Docker!"`

d. `docker start <container>`: Start a stopped container.

e. `docker stop <container>`: Stop a running container.

f. `docker restart <container>`: Restart a container.

g. `docker rm <container>`: Remove a container.

h. `docker container prune`: Remove all stopped containers.

1. Container Logs and Executing Commands:
    

a. `docker logs <container>`: Display the logs of a container. Example: `docker logs mycontainer`

b. `docker exec -it <container> <command>`: Execute a command in a running container. Example: `docker exec -it mycontainer bash`

1. Networking:
    

a. `docker network ls`: List all networks.

b. `docker network create <network>`: Create a new network.

c. `docker network connect <network> <container>`: Connect a container to a network.

1. Volume Management:
    

a. `docker volume ls`: List all volumes.

b. `docker volume create <volume>`: Create a new volume.

c. `docker volume inspect <volume>`: Display detailed information about a volume.

d. `docker volume rm <volume>`: Remove a volume.

1. Docker Compose:
    

a. `docker-compose up`: Start containers defined in the Compose file.

b. `docker-compose down`: Stop and remove containers defined in the Compose file.

c. `docker-compose logs <service>`: Display the logs of a specific service defined in the Compose file.

## Guidance into Docker

1. Understand the Basics: Familiarize yourself with the core concepts of Docker, such as containers, images, and Dockerfiles. Understand how containers provide isolation and portability for applications, and how images serve as the building blocks for containers. Learn how to create a Dockerfile to define the configuration and dependencies of your application.
    
2. Install Docker: Visit the official Docker website ([**https://www.docker.com/**](https://www.docker.com/)) and download the appropriate version of Docker for your operating system. Follow the installation instructions to set up Docker on your machine.
    
3. Learn Docker Commands: Start by learning some essential Docker commands, such as pulling images, running containers, and managing images and containers. Refer to the commands mentioned in the previous response for a starting point.
    
4. Dockerize Your Application: Identify an application or service that you want to containerize with Docker. Create a Dockerfile in the root directory of your application. In the Dockerfile, specify the base image, copy the necessary files, set environment variables, and define the commands needed to run your application. Build an image using the Dockerfile and test it locally.
    
5. Explore Docker Hub: Docker Hub is a registry of Docker images where you can find a wide range of pre-built images for various technologies. Explore Docker Hub to find images related to your application's stack, such as databases, web servers, or programming languages. Pull and use these images in your Docker environment.
    
6. Practice with Containers: Experiment with running containers using different images and configurations. Use the `docker run` command to start containers based on specific images. Gain familiarity with container lifecycles, such as starting, stopping, and removing containers. Monitor logs and execute commands within running containers.
    
7. Networking and Volumes: Understand how Docker handles networking and storage. Learn how to create and manage networks to enable communication between containers. Explore Docker volumes to persist data generated by your containers or to share data between containers and the host system.
    
8. Docker Compose: Docker Compose simplifies the management of multi-container applications. Learn how to define services, networks, and volumes using a YAML file. Use Docker Compose to start, stop, and manage your application stack as a whole.
    
9. Explore Advanced Topics: Once you have a solid understanding of the basics, dive into more advanced Docker topics, such as Docker Swarm for orchestration, Dockerfile best practices, multi-stage builds, container security, and containerizing different types of applications.
    
10. Join the Docker Community: Engage with the Docker community by joining forums, attending meetups, or participating in online discussions. Share your knowledge and learn from others' experiences. The Docker community is vibrant and supportive, and you can find valuable insights and solutions to various Docker-related challenges.