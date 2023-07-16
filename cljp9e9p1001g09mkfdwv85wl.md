---
title: "Docker Project"
datePublished: Wed Jul 05 2023 05:09:07 GMT+0000 (Coordinated Universal Time)
cuid: cljp9e9p1001g09mkfdwv85wl
slug: docker-project
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688533673279/261c5e7f-65d0-4b8b-a971-f3ff4aacc6f3.png
tags: docker, docker-images, wemakedevs, dockerprojects

---

# **Dockerfile**

Docker is a tool that makes it easy to run applications in containers. Containers are like small packages that hold everything an application needs to run. To create these containers, developers use something called a Dockerfile.

A Dockerfile is like a set of instructions for making a container. It tells Docker what base image to use, what commands to run, and what files to include. For example, if you were making a container for a website, the Dockerfile might tell Docker to use an official web server image, copy the files for your website into the container, and start the web server when the container starts.

![](https://miro.medium.com/v2/resize:fit:641/1*SldhABVOKsX_6L70iA3E2w.png align="left")

# **TASKS:**

* **Create a Dockerfile for a simple web application (e.g. a Node.js or Python app)**
    

Before moving forward with the creation of Dockerfile, you need to install docker in your server. We have seen the steps to install docker in the previous article (Day 16).

Link is below:

## [**How to install Docker on Amazon Linux 2**](https://swapnasagarpradhan.medium.com/how-to-install-docker-on-amazon-linux-2-8e5161ac5464)

* **Build the image using the Dockerfile and run the container**
    
* **Verify that the application is working as expected by accessing it in a web browser**
    
* **Push the image to a public or private repository (e.g. Docker Hub )**
    

For this you first need a AWS EC2 instance of your own choice.

Once you are done with creating a EC2 instance you need to SSH into it.

Below are the steps that we will be going to perform in the process:

1. Install Git and clone the repo of the Node.js application
    
2. Install Docker
    
3. Create and configure a Dockerfile
    
4. Build a Docker image
    
5. Create and run a Docker container
    
6. Access it
    

# **1\. Clone the repo of the Node.js application**

Open the instance, first you need to install Git in it so that we can clone the application repository from the GitHub(VCS). Use command :

```bash
#yum install git -y
```

![](https://miro.medium.com/v2/resize:fit:700/0*jD24SxN3s0L7LQ_7.png align="left")

Now clone the application repository, using the command :

```bash
#git clone https://github.com/rajani103/nodejs-on-ec2.git (git URL of repo)
```

![](https://miro.medium.com/v2/resize:fit:700/0*LFnRPPGXsAej6qOT.png align="left")

# **2\. Install Docker**

Install Docker in the machine using the command :

```bash
#yum install docker -y
```

![](https://miro.medium.com/v2/resize:fit:700/0*EUuMvTPjPweLE7Eh.png align="left")

Now check the version of the docker once and start the docker and check the status of the docker to know if it is running using the below commands :

```bash
#docker -v 
#systemctl start docker
#systemctl status docker
```

![](https://miro.medium.com/v2/resize:fit:700/0*LGJG8ZNEvqi1epY0.png align="left")

# **3\. Create and configure a Dockerfile**

Now we will create and configure a dockerfile as per the requirement of the Node.js application. Change the directory to the cloned project and create Dockerfile there.

Here is the Dockerfile that I have created :

```bash
FROM node:16
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 80
CMD ["node", "index.js"]
```

You can check my previous blog for understanding the Dockerfile.

![](https://miro.medium.com/v2/resize:fit:700/0*zGdIhlUVUozpUAng.png align="left")

# **4\. Build a Docker image**

Now before starting the build process check if there is any existing container running with the same name.

Use command :

```bash
#docker ps
#docker ps -a
```

Now you are all set to build the image. Use command :

```bash
# docker build . -t app
```

![](https://miro.medium.com/v2/resize:fit:700/0*g0zDUK_4GxqcdH4m.png align="left")

![](https://miro.medium.com/v2/resize:fit:700/0*3nfHSYdN-t3zvAaP.png align="left")

# **5\. Create and run a Docker container**

Using the image that has been built we will create a container out of it and run it:

Use the below commands :

```bash
# docker run -d --name nodejs-app-cont -p 80:80 app:latest
```

You can see a container running here which can be accessed on port 80 as we have done the port mapping on port 80.

![](https://miro.medium.com/v2/resize:fit:700/0*Kqsbwhpod4BwfbQP.png align="left")

# **6\. Access it**

Now you can take the public IP of the machine and port 80 to access the application.

![](https://miro.medium.com/v2/resize:fit:700/0*umoeBgzt4E1RhbbL.png align="left")

And yess!! it is accessible.🌻✨

# **7\. Pushing the image on DockerHub**

We have already created a Docker image using the Dockerfile. Check all the images present by using the command.

```bash
docker images
```

Now we will login into the DockerHub by adding the command:

```bash
Docker login
```

Put your username and password here. If the login is successful, then you will get a message like **Login Succeeded**.

Now tag the locally created image to the docker hub. This means we have to tag the image with the docker hub username.

```bash
docker tag app:latest rajjo103/app:latest
```

Now push the image to the Docker hub using the push command.

```bash
docker push rajjo103/app:latest
```

And it is done, you can check in your Docker hub if it is pushed.