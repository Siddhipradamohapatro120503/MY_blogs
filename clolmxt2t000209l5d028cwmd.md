---
title: "Deploying Nginx Server on AWS"
datePublished: Sun Nov 05 2023 15:35:40 GMT+0000 (Coordinated Universal Time)
cuid: clolmxt2t000209l5d028cwmd
slug: deploying-nginx-server-on-aws
tags: aws, nginx, cloud-computing, aws-cdk, nginx-configuration-guide

---

# Introduction

**NGINX** is open-source software for web serving, reverse proxying, caching, load balancing, media streaming, and more. It started out as a web server designed for maximum performance and stability. In addition to its HTTP server capabilities, NGINX can also function as a proxy server for email (IMAP, POP3, and SMTP) and a reverse proxy and load balancer for HTTP, TCP, and UDP servers.

### Steps

**Step1: First login to Aws Console and navigate to the Search bar for Ec2**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698760095103/74ccaf84-2207-45c8-9282-0dd4147e1a59.png align="center")

**Click to Launch Instance**

Give a Name to a webserver and choose Ubuntu from Amazon Machin Image(AMI)

Take Instance Type T2.micro (free tier Eligible)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698760385884/53ec4987-3cc4-40d0-a2b0-3791dace3d33.png align="center")

**Step2: Make sure to make a PEM file for Instance It is a Key for login Into the instance**

**Leave All the things Default**

**<mark>The click on Launch Instance</mark>**

**Click On Instance ID**

**Step 3: Go to connect &lt; SSH client then Copy the example Code and past It on the CMD of the Download folder because Our key was downloaded in that folder**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698760840399/cd531022-9975-4575-9758-a826f9dc9693.png align="center")

**Type YES**

**Step 4: Download Nginx**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698760960959/64079fcd-636b-4e7a-bb93-aef7d14f58cd.png align="center")

**Make sure to update the system**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698761089181/0aa2a720-36dd-4655-af2b-a6dd0399d801.png align="center")

```bash
suod apt install nginx -y
```

```bash
sudo systemctl start nginx
```

**Step 4: Our Nginx server runs on port 80 which is HTTP we Enable that for ec2 Instance In Security Groups**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698761352741/77e16f48-7bb5-4e18-bfc6-b3ab15f9bb1b.png align="center")

<mark>Click on Save Rules</mark>

**Copy the Public IP of the Instance And Boom**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698761607453/6ffc55d5-24db-4aac-99e0-c33285453ac4.png align="center")

😊 Thank you so much for reading my blog! 😊 I hope you found it helpful and informative. If you did, please 👍 give it a like and 💌 subscribe to my newsletter for more of this type of content. 💌

I'm always looking for ways to improve my blog, so please feel free to leave me a comment or suggestion. 💬

Thanks again for your support!