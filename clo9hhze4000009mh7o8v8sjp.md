---
title: "Simple DevOps Project: Deployment of 2048 Game on AWS using docker"
datePublished: Sat Oct 28 2023 03:30:10 GMT+0000 (Coordinated Universal Time)
cuid: clo9hhze4000009mh7o8v8sjp
slug: simple-devops-project-deployment-of-2048-game-on-aws-using-docker
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698167530223/c1ff46a7-c547-408f-982b-0caaa3920113.gif
tags: cloud, docker, aws, docker-images, aws-certified-solutions-architect-associate

---

### **Introduction**

This application was deployed in the Ec2 instance of Ubuntu's Processor of T2 Micro with 8 GB of storage on it.

Setup:

1. **Launch an EC2 instance.**
    
    * Sign in to the AWS Management Console.
        
    * Go to the EC2 Dashboard.
        
    * Click on "Launch Instance."
        
    * Choose an Amazon Machine Image (AMI) with Ubuntu, such as "Ubuntu Server" or "Ubuntu LTS."
        
    * Select an instance type, configure instance details, and add storage as needed.
        
    * Configure security groups to allow SSH (port 22) and any other required access.
        
    * Review and launch the instance, and create or choose an existing key pair to connect to the instance securely.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698165244153/d0b1a224-6631-4a2f-81eb-bf660efd2e38.png align="center")
        
2. **Connect to the EC2 instance**:
    
    Once your EC2 instance is running, you can connect to it using SSH. Replace `your-key.pem` with the actual name of your key pair file and `your-instance-ip` with the public IP of your instance:
    
    ```bash
    ssh -i your-key.pem ubuntu@your-instance-ip
    ```
    
3. **Update and Upgrade Packages**:
    
    After connecting to the instance, it's a good practice to update and upgrade the system packages to ensure you have the latest software and security updates:
    
    ```bash
    sudo apt update
    sudo apt upgrade
    ```
    
4. We have to install Docker.
    
    ```bash
    sudo apt install docker.io -y
    ```
    
5. We have given permission to docker
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698164877585/5e435d84-cdbf-4a40-9232-3d9d4c4dd838.png align="center")
    
6. Then we will write a Dockerfile for our 2048 app
    
    ```bash
    FROM ubuntu:22.04
    RUN apt-get update
    RUN apt-get install -y nginx zip curl
    RUN echo "daemon off;">>/etc/nginx/nginx.conf
    RUN curl -o /var/www/html/master.zip -L https://codeload.github.com/jabir000/2048/zip/master
    RUN cd /var/www/html/ && unzip master.zip && mv 2048-master/* . && rm -rf 2048-master master.zip
    EXPOSE 80
    CMD ["/usr/sbin/nginx", "-c", "/etc/nginx/nginx.conf"]
    ```
    
    1. Execute the following commands in the new terminal
        
        ```bash
        pwd
        
        ls
        
        docker build -t <docker image name> .
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698165021927/90a381a4-f0a8-47da-914d-444804e6e128.png align="center")
        
        ```bash
        docker images
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698165073042/8c2f1c39-c4f1-4431-99a0-bed3de4fd3aa.png align="center")
        
        ```bash
        docker run -d -p 80:80 <container id>
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698165119379/9f25fbde-e548-4005-a710-e71b2c4d2030.png align="center")
        
        ```bash
        docker ps
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698165165685/a54c55e6-e962-4190-9a73-6a801a3d814d.png align="center")
        

😊 Thank you so much for reading my blog! 😊 I hope you found it helpful and informative. If you did, please 👍 give it a like and 💌 subscribe to my newsletter for more of this type of content. 💌

I'm always looking for ways to improve my blog, so please feel free to leave me a comment or suggestion. 💬

Thanks again for your support! 😊