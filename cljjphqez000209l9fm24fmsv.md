---
title: "Deploying a web application using Nginx server and Reverse Proxy"
datePublished: Sat Jul 01 2023 07:53:05 GMT+0000 (Coordinated Universal Time)
cuid: cljjphqez000209l9fm24fmsv
slug: deploying-a-web-application-using-nginx-server-and-reverse-proxy
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688302993113/4afa1773-6998-4955-a241-e23e2296eef0.png
tags: ec2, aws, cloud-computing, ecs, eks-cluster

---

### **What is Nginx?**

Nginx is a popular open-source web server software which serves its clients web pages. Suppose you want to access some website ([www.google.com](http://www.google.com)), when you put this web address in the browser you will see the homepage(web-page) of google. Web server serves the web files i.e. the HTML, CSS, Javascript files to the client i.e. user.

In short it is a web server which serves the web pages to its clients as per the need and requirement.

Nginx is compatible with multiple operating systems, including Linux, Windows, and macOS, and it is commonly used alongside other web technologies such as PHP, Python, and Ruby on Rails.

### **Why Nginx ?**

1. High performance: Nginx is known for its high performance and low resource usage. It is designed to handle a large number of concurrent connections and requests, making it a great choice for high-traffic websites and web applications.
    
2. Scalability: Nginx can be easily scaled horizontally by adding more servers to handle increased traffic. It also supports load balancing, which distributes traffic evenly across multiple servers.
    
3. Flexibility: Nginx has a modular architecture, which means that it can be easily extended and customized with various modules to suit different needs.
    
4. Security: Nginx has built-in security features such as SSL/TLS encryption and support for secure communication protocols. It also has the ability to block malicious traffic and prevent common attacks such as DDoS attacks.
    
5. Ease of use: Nginx is relatively easy to set up and configure compared to other web server software.
    

### **Architecture of Nginx**

![](https://miro.medium.com/v2/resize:fit:700/1*_YaAlLi0cCnuk1OnsxpicQ.jpeg align="left")

Nginx architecture consists of a master process and multiple child processes i.e. worker processes. These multiple child processes helps in managing the load on the server by distributing the traffic towards multiple worker processes.

Suppose if you have a website running on a particular port and many people tried to access the same then at a point the website will crash because it will not be able to take the load.

To overcome this if you served the website through Nginx server then the server will distribute the load in it’s multiple child processed and hence there won’t be any crash and the website will work smoothly.

Overall, the architecture of Nginx is designed to provide high performance and scalability while remaining flexible and easy to configure.

### **More features of Nginx**

## **Reverse Proxy**

Suppose there is a website running on a particular port on local host and you want it to run on the production without violating the security then we can use the reverse proxy and can create a bridge and make the port accessible to all the users.

A reverse proxy is a server that sits between client devices and one or more web servers, forwarding client requests to the appropriate server and returning the server’s response to the client. The client is unaware that the response is coming from a different server than the one it sent the request to.

## **Load Balancing**

It is a technique used to distribute incoming network traffic across multiple servers to ensure high availability and reliability of a service.

## **URL Redirection, Indexing, Caching**

URL redirection is the process of forwarding one URL to another.

Indexing is the process of adding web pages to a search engine’s database so that they can be returned in search results.

Caching is the process of storing frequently accessed data in a cache so that it can be served more quickly.

# **Hands-On**

![](https://miro.medium.com/v2/resize:fit:700/1*tA5B__wmPmvC6dteWr0-Cg.png align="left")

Flowchart

First you need to create an AWS EC2 instance. I have selected Ubuntu image while creating the EC2 instance. Add inbound traffic rules for HTTP, and HTTPS.

![](https://miro.medium.com/v2/resize:fit:700/1*4HLFIHBhMYM7Fg-EWtLBtw.png align="left")

After this SSH into the instance.

Then you need to update the instance. Use command :

```bash
sudo apt-get update
```

![](https://miro.medium.com/v2/resize:fit:700/1*7IuAsTZ6PYxL1FXQ6SxkcA.png align="left")

Now we need to install Nginx. Use command:

```bash
sudo apt install nginx
```

![](https://miro.medium.com/v2/resize:fit:700/1*1gNGZM-dWCGcAPBZkRX3Aw.png align="left")

Check if the Nginx is in running state. Use command:

```bash
systemctl status nginx
systemctl restart nginx 
(if asked for password do sudo systemctl restart nginx)
```

![](https://miro.medium.com/v2/resize:fit:700/1*zCDk-RTMVozO5NSMDiPvEg.png align="left")

Also you can take the public IP of the server and try accessing it in browser,to check if the Nginx is installed properly.

![](https://miro.medium.com/v2/resize:fit:700/1*Lw9aN7ttNPlHjISlXOn8vg.png align="left")

This page is been accessed from /var/www/html

![](https://miro.medium.com/v2/resize:fit:700/1*HzoZoa3OuEuBrYzZ28jRIg.png align="left")

You can check the Nginx configuration files here:

![](https://miro.medium.com/v2/resize:fit:700/1*vzoX8wjwoUCYPxcsE6dcTA.png align="left")

![](https://miro.medium.com/v2/resize:fit:700/1*4NStPp30j0iroW-nBIwOrQ.png align="left")

If you want to deploy some application you can go to /var/www/html and create an index.html file and add your html code and and you can access the same using the public IP of the server.

Check on the browser by putting the IP address. You will see below home page.

![](https://miro.medium.com/v2/resize:fit:700/1*vtlh3RQlSosvinbhH4f8KQ.png align="left")

Now clone the source code repository. Use command:

```bash
git clone https://github.com/rajani103/django-notes-app.git
```

![](https://miro.medium.com/v2/resize:fit:700/1*KUL9qDB3_BU2V4Hyh6fm6w.png align="left")

Now install docker. Use command:

```bash
sudo apt install docker.io
```

Check docker status:

![](https://miro.medium.com/v2/resize:fit:700/1*9l9emY8kJT_PvLBywDccCA.png align="left")

Now check if docker is working fine.

![](https://miro.medium.com/v2/resize:fit:700/1*hqWmXcGCT8B0qfMfFPYqTg.png align="left")

Permission denied because this user doesn’t have access to docker . So we will give this user permission. Use command:

```bash
sudo usermod -aG docker $USER

$USER == current logged in user
```

After this reboot the server.

```bash
sudo reboot
```

Here is the Dockerfile :

```bash
FROM python:3.9

WORKDIR /app/backend

COPY requirements.txt /app/backend
RUN pip install -r requirements.txt

COPY . /app/backend

EXPOSE 8000

CMD python /app/backend/manage.py runserver 0.0.0.0:8000
```

Now we will start the build process of the application. Use command :

```bash
docker build -t notes-app .
```

![](https://miro.medium.com/v2/resize:fit:700/1*azC4d2VXIkmgjINws7BIYA.png align="left")

The image has been created successfully.

![](https://miro.medium.com/v2/resize:fit:670/1*kQNUlgAkdNPWfYQjrj2S_w.png align="left")

Now using this image we will create a container . Use below command:

```bash
docker run -d -p 8000:8000 notes-app:latest
```

![](https://miro.medium.com/v2/resize:fit:700/1*jp-4XQAQgIzSCUX_zfGXTQ.png align="left")

Now do #docker ps and check if the container is created properly and it has been tagged to the 8000 port so that we can access the sameon that port.

![](https://miro.medium.com/v2/resize:fit:700/1*NCJeoFXeIvl_NFKPnzDc8g.png align="left")

This application is now running on the local host and we can check it using the command:

```bash
curl -L <local_url>:<External-Ip>
curl -L http://127.0.0.1:8000
```

![](https://miro.medium.com/v2/resize:fit:700/1*VWWl33CLzdWcrIMvv80TaQ.png align="left")

But we want to give access to the application by using the concept of reverse proxy so that the clients can access the same.

For this we need to change the configuration of Nginx so for that go to /etc/nginx/sites-enabled

![](https://miro.medium.com/v2/resize:fit:700/1*WPE7cubbxNDhYQ9SgvbkTQ.png align="left")

Now we will update the default file for changing the configuration.

![](https://miro.medium.com/v2/resize:fit:700/1*stD6zC8kUqpUztth0XuDCA.png align="left")

Here we have added a proxy address for the incoming traffic.

After adding this you need to restart the nginx so that the updates will work. Use below command to restart nginx.

```bash
sudo service nginx restart
```

Now you can access the application using the IP address.

![](https://miro.medium.com/v2/resize:fit:480/1*taFiEDsg9zXC9vr7nc4tbw.png align="left")

Now the app is accessible but we are not able to update or delete the notes here because the backend code is not updated here to store such data.

For this we need to copy all the static files of the application to the location Nginx root folder /var/www/html so that we can access it.

Use command :

```bash
sudo cp -r * /var/www/html/
```

![](https://miro.medium.com/v2/resize:fit:700/1*pmkwnrBAIgHeFPXCZ6WQag.png align="left")

![](https://miro.medium.com/v2/resize:fit:700/1*w1cqI7IKDe6NCtBy7nulJg.png align="left")

Now we need to update the location /api for the backend page of the server.

Go to /etc/nginx/sites-enabled location and update the code.

![](https://miro.medium.com/v2/resize:fit:700/1*gZ_Z6Tj3_mzqCaX_DpAheg.png align="left")

Save it and you need to restart the service.