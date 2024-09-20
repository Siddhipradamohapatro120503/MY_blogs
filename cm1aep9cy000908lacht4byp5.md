---
title: "The Ultimate Starters Guide to Nginx"
datePublished: Fri Sep 20 2024 07:35:47 GMT+0000 (Coordinated Universal Time)
cuid: cm1aep9cy000908lacht4byp5
slug: the-ultimate-starters-guide-to-nginx
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1726817733332/31f08ad7-0c35-4578-9f74-99d3760cf88e.png

---

# **Introduction**

Nginx (pronounced “engine x”) is one of the most popular open-source web server technologies. Its use cases range from serving static webpages to acting as a full fledged load balancer. Nginx is commonly chosen when performance and scalability are most important.

The need to handle a large number of requests dates back to Nginx’s inception. It was initially developed to solve the C10k problem. “The C10k problem is the problem of optimizing [network sockets](https://en.wikipedia.org/wiki/Network_socket) to handle a large number of clients at the same time.” \[2\] To do this, Nginx utilizes an event-driven asynchronous approach, which allows it to handle a large number of concurrent requests and still maintain a predictable performance level.

This event-driven architecture allows for multiple requests to be handled per thread, whereas other technologies such as Apache, require a dedicated thread per request. This leads to Nginx being much more scalable and using considerably less memory.

## **Goals of This Article**

The main purpose of this article is to give a hands on tutorial of how you can start using Nginx right away. I will first explain how to install Nginx, and exactly what directories/files you should be most aware of. Next, I will show how to host a very basic static website using Nginx. Then, I will setup a reverse proxy server to route incoming requests on port 80 over to port 5000 where a flask application is running. Finally, I will explain how to enable SSL on an Nginx server with the help of Certbot and Let’s Encrypt.

# **Setup & Preparation**

## **EC2 Setup**

The EC2 instance required for this demo is very straight-forward. I will be using an Amazon Linux 2023 t2.micro. During setup, the only modification from the default needed is to enable http/https traffic from the internet.

![](https://miro.medium.com/v2/resize:fit:700/1*arPdgjAgaWb_TIclM7LAaQ.png align="left")

Security Group Settings

## **Elastic IP**

Next, I will obtain an Elastic IP address and associate it to this instance. Without it, the public IP address of the instance will change each time its restarted.

First allocate the IP, which basically means to obtain it.

![](https://miro.medium.com/v2/resize:fit:700/1*_2XZZZxj_F96md0cuPVV4w.png align="left")

Then, associate the IP with the EC2 we just created.

![](https://miro.medium.com/v2/resize:fit:700/1*0n_ZOrls6e9LAPxYY5yOjQ.png align="left")

Now if you observe the public IP of the instance, it will match the Elastic IP.

![](https://miro.medium.com/v2/resize:fit:522/1*NWYdDwrXD_8bG1YGDVfH-g.png align="left")

## **Install Nginx**

Once deployed, Nginx can be installed on the EC2 with the following command: `sudo yum install nginx`. Previously, I had installed nginx from amazon-linux-extras repository, however now with the release of Amazon Linux 2023, you can just simply install with yum. Below I will check the version that was installed, and then start the service and finally check its status to see if its running.

```plaintext
~$ nginx -v

nginx version: nginx/1.22.1

~$ sudo systemctl start nginx

~$ sudo systemctl status nginx

nginx.service - The nginx HTTP and reverse proxy server
     Loaded: loaded (/usr/lib/systemd/system/nginx.service; disabled; preset: disabled)
     Active: active (running) since Sat 2023-03-18 14:20:18 UTC; 30s ago
    Process: 25963 ExecStartPre=/usr/bin/rm -f /run/nginx.pid (code=exited, status=0/SUCCESS)
    Process: 25965 ExecStartPre=/usr/sbin/nginx -t (code=exited, status=0/SUCCESS)
    Process: 25966 ExecStart=/usr/sbin/nginx (code=exited, status=0/SUCCESS)
   Main PID: 25967 (nginx)
      Tasks: 2 (limit: 1125)
     Memory: 2.2M
        CPU: 57ms
     CGroup: /system.slice/nginx.service
             ├─25967 "nginx: master process /usr/sbin/nginx"
             └─25968 "nginx: worker process"

Mar 18 14:20:18 ip-XXXXXXX.us-east-2.compute.internal systemd[1]: Starting nginx.service - The nginx HTTP and reverse proxy server...
Mar 18 14:20:18 ip-XXXXXXX.us-east-2.compute.internal nginx[25965]: nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
Mar 18 14:20:18 ip-XXXXXXX.us-east-2.compute.internal nginx[25965]: nginx: configuration file /etc/nginx/nginx.conf test is successful
Mar 18 14:20:18 ip-XXXXXXX.us-east-2.compute.internal systemd[1]: Started nginx.service - The nginx HTTP and reverse proxy server.
```

Now, if we navigate the the public IP address of this instance, we can confirm Nginx is running:

![](https://miro.medium.com/v2/resize:fit:700/1*tT-t-t4vp5T_oQq-HyHQCg.png align="left")

## **Route 53 Record Setup**

The final prep we need to do before diving in is to create domain records for each of the examples that will be covered later. I will assume that the reader already has a hosted zone setup under route 53. If not, you will have to purchase a domain name and then configure your hosted zone prior to moving forward.

My base domain is ericjflynn.com. For the examples, I will be adding two A records for subdomains within this hosted zone so that I don’t have to purchase a new domain. They will be static-site.ericjflynn.com and flask-app.ericjflynn.com respectively. Make sure that the routing values for these records point to the Elastic IP address from before.

![](https://miro.medium.com/v2/resize:fit:700/1*9foodonvWCmxvu1MZHUL0Q.png align="left")

Give the record a minute to propagate, and then when navigating to static-site.ericjflynn.com, you can see I’m getting the same page. Now we know that the routing is working properly!

![](https://miro.medium.com/v2/resize:fit:700/1*cFmicx5lLZ3MooYyBR5PVw.png align="left")

*The same steps are followed for flask-app.ericjflynn.com*

# **Default Nginx**

Upon installation of Nginx on your machine, a directory is created at `~/etc/nginx`. See below for the directory structure. For now, ignore everything except for the `nginx.conf` file and the `conf.d` directory. Any file ending in `.conf` indicates an Nginx configuration file and `~/etc/nginx/nginx.conf` is the default configuration file. Later, we will utilize the `conf.d` directory to store our custom configuration files.

```plaintext
├── conf.d
├── default.d
├── fastcgi.conf
├── fastcgi.conf.default
├── fastcgi_params
├── fastcgi_params.default
├── koi-utf
├── koi-win
├── mime.types
├── mime.types.default
├── nginx.conf
├── nginx.conf.default
├── scgi_params
├── scgi_params.default
├── uwsgi_params
├── uwsgi_params.default
└── win-utf
```

## **Investigating the Default nginx.conf File**

Now that we know Nginx is successfully running, lets dig into why. As stated previously, the default configuration file is located at `~./etc/nginx/nginx.conf`. This file will determine how traffic gets routed upon being received by the server and what response will be provided. Below, observe a subset of the `nginx.conf` file:

```plaintext
    server {
        listen       80;
        listen       [::]:80;
        server_name  _;
        root         /usr/share/nginx/html;
```

As you can see, a “server” is being defined. This server will listen for requests on port 80 at server\_name “\_” and then serve the files from the root `usr/share/nginx/html` folder. The server name “\_” acts as the default server name and will catch for all server names routing to this instance until another server block has been defined.

Upon opening the `index.html` file from that folder, you can see it matches the webpage shown before.

```plaintext
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

# **Custom Configuration for Static Site Hosting**

Now that we’ve investigated the default configuration, its time to setup a custom configuration to serve static content. Whenever someone visits the static-site.ericjflynn.com domain, we would like to serve them a specific webpage.

## **Creating a Custom Configuration File**

As stated earlier, new configuration files will be created in the `~/etc/nginx/nginx.d` folder. I will now cd into this folder, and use vim to create the following file `static-site.conf`*.* (Make sure to use **sudo** vim)

```plaintext
server {
        listen 80;
        server_name static-site.ericjflynn.com;
        root /var/www/static-site;
        index index.html;
        location / {
                try_files $uri $uri/ =404;
        }
}
```

This configuration will listen for requests on port 80 which originate with the domain name “static-site.ericjflynn.com”. These requests will then serve files from the root location `var/www/static-site` which I will create in the coming steps.

Now that the configuration file has been created, its time to create the `~/var/www/static-site` directory and then define the `index.html` that is going to be served.

```plaintext
~$ cd /var

~$ sudo mkdir www && cd www

~$ sudo mkdir static-site && cd static-site

~$ sudo vim index.html
```

```plaintext
#index.html
<h1>Hello, welcome to my static site being served with Nginx!</h1>
```

Now, I will restart the Nginx service with `sudo systemctl reload nginx`, and then visit static-site.ericjflynn.com. As you can see, it is now serving my custom index.html document!

![](https://miro.medium.com/v2/resize:fit:700/1*8NVAIy2-MET5a0r17elh5w.png align="left")

# **Reverse Proxy Server for Flask Application**

For this section, I will cover how to configure the Nginx server to serve a Flask application running on port 5000 to users visiting the site on port 80. This will run on the same instance, which is still serving the static site.

## **Install tmux**

Before setting up the Flask app, I am going to install tmux, which is short for terminal multiplexer. This allows you to run an independent terminal for your Flask application while still being able to use another terminal simultaneously for configuration and setup. To install simply use `sudo yum install tmux`. To activate, type `tmux` and it will bring you to a separate terminal instance. To detach, enter cntrl+b then d. To re-attach at any time, simply type `tmux attach`.

## **Setting Up The Flask App**

To setup the flask app, I will first create a directory for it, and then initiate a virtual environment. Then I will activate this environment and install flask.

```plaintext
~$ mkdir flask-app && cd flask-app

flask-app $ python3 -m venv venv

flask-app $ source venv/bin/activate

(venv) flask-app $ pip install flask
```

Now that the environment is ready, I will use vim to create the following file:

```plaintext
#app.py
from flask import Flask

app = Flask(__name__)

@app.route('/')

def hello():
    return '<h1>Hello from a flask app!</h1>'
```

Now that the environment is all ready, I will initiate a tmux environment and run the Flask application.

```plaintext
(venv) flask-app $ tmux

(venv) flask-app $ flask --app app run

 * Serving Flask app 'app'
 * Debug mode: off
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on http://127.0.0.1:5000
Press CTRL+C to quit
```

## **Configure Nginx Reverse Proxy**

To setup the Nginx configuration for the Flask app, first cd into `~/etc/nginx/conf.d` directory and use vim (sudo) to create a new file `flask-app.conf`. This configuration will also listen on port 80 for traffic, however the server\_name here is now for the flask-app.ericjflynn.com domain. In the location, I specified a proxy-pass to the port on which the flask application is running. (This can be seen in the output above as well)

```plaintext
#flask-app.conf
server {
        listen 80;
        server_name flask-app.ericjflynn.com;

location / {
        proxy_pass http://127.0.0.1:5000;
        }
}
```

Now, save the file and reload Nginx with `sudo systemctl reload nginx`. We can now navigate to the server\_name and see that the application is running properly.

![](https://miro.medium.com/v2/resize:fit:700/1*wC7BrjxuklGjipdcj-r_CA.png align="left")

If I now go back to static-site.ericjflynn.com, you can see that the original site is still running properly.

![](https://miro.medium.com/v2/resize:fit:700/1*xmUZ_8DhgrHBuQiogq9NpQ.png align="left")

# **SSL with Let’s Encrypt and Certbot**

Enabling SSL is a must for any modern webpage. Let’s Encrypt is the free-use certificate authority provided by the Electronic Frontier Foundation as part of their goal to encrypt the entire internet. The goal of this service is to automate the configuration of SSL certificates with minimal human intervention. Let’s Encrypt uses Certbot as its client, which is what I will be using in this demo.

> *Certbot is not officially supported on Amazon Linux 2023, but is available for download and functions correctly when installed. \[7\]*

## **Install Certbot**

To install Certbot on Amazon Linux 2023, unfortunately its not as simple as just a yum install. This is because Certbot is not included by default in the Amazon Linux 2023 repository. Below, I will be installing Certbot into a Python virtual environment with pip. This is the process that was recommended in the official [AWS documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/SSL-on-amazon-linux-2023.html).

1. Install EPEL Releases
    

```plaintext
~$ sudo yum install -y python3 augeas-libs pip
```

2\. Create Virtual Environment In New Directory

```plaintext
~$ sudo python3 -m venv /opt/certbot/
```

3\. Update pip

```plaintext
~$ sudo /opt/certbot/bin/pip install — upgrade pip
```

4\. Install Certbot

```plaintext
~$ sudo /opt/certbot/bin/pip install certbot
```

5\. Add Symbolic Link (Allows you to use `certbot` command from anywhere)

```plaintext
~$ sudo ln -s /opt/certbot/bin/certbot /usr/bin/certbot
```

## **Run Certbot**

Now that certbot is installed, I will use it to create an SSL certificate for my domains.

```plaintext
sudo certbot certonly — standalone
```

Certbot will now prompt you to enter your email for where to receive renewal notifications and optional marketing information. Then you must accept the terms and conditions. Finally, you will be prompted to enter the domain name(s) requesting an SSL certificate. In this case, used the same SSL certificate for both of my domains so I entered them in a comma separated list. After finishing all the instructions, take note of where the certifications are stored, as this will be used later:

`/etc/letsencrypt/live/<domain-name>`

## **Update Nginx Configuration**

Now that the certificates have been obtained, it’s time to update the Nginx configuration to enable SSL traffic. See below for the updated `static-site.conf` file.

```plaintext
server {
        listen 80;
        server_name static-site.ericjflynn.com;
        location / {
                return 301 https://$server_name$request_uri;
        }
}
server {
        listen 443 ssl;
        server_name static-site.ericjflynn.com;
        ssl_certificate /etc/letsencrypt/live/static-site.ericjflynn.com/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/live/static-site.ericjflynn.com/privkey.pem;
        add_header Strict-Transport-Security “max-age=31536000”;
        root /var/www/static-site;
        index index.html;
        location / {
                try_files $uri $uri/ =404;
        }
}
```

As you can see, now when traffic is being received at port 80, its being re-routed to the https version of the requested server\_name. This will automatically then be received at port 443 which is the default SSL port. This configuration is now very similar to how it was previously under port 80, but now you must point Nginx to where the ssl\_certificate and ssl\_certificate\_key are stored. This is the path I previously took note of. I also added a header “Strict-Transport-Security” to ensure no connection is made without SSL.

Before proceeding, be sure to reload the Nginx service with `sudo systemctl reload nginx`. Now if I navigate to the same domain, static-site.ericjflynn.com, I will be directed to an https secured site. This is confirmed from the lock in the search bar. Note: Even when explicitly typing http:// I am still being redirected to the https:// endpoint as I defined in the configuration.

![](https://miro.medium.com/v2/resize:fit:700/1*_eX_MYe2uVgOYO5QNX4-jw.png align="left")

I can now perform the same process for my flask-app. The new configuration file will look as below:

```plaintext
server {
        listen 80;
        server_name flask-app.ericjflynn.com;
        location / {
                return 301 https://$server_name$request_uri;
        }
}
server {
        listen 443 ssl;
        server_name flask-app.ericjflynn.com;
        ssl_certificate /etc/letsencrypt/live/static-site.ericjflynn.com/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/live/static-site.ericjflynn.com/privkey.pem;
        add_header Strict-Transport-Security "max-age=31536000";
        location / {
                proxy_pass http://127.0.0.1:5000;
        }
}
```

This is very similar to how it was done in transitioning the static site over, but with one key difference. Take special note that the path to the ssl\_certificate and ssl\_certificate\_key is exactly the same as in the `static-site.conf`. This is because I elected to have both of these domains share the same certificate. After navigating to flask-app.ericjflynn.com, I can confirm this works properly.

![](https://miro.medium.com/v2/resize:fit:700/1*SYv5vzRLqF8saFeGALk45g.png align="left")

## **Configure Auto Renewal For Certs**

The last topic I’d like to cover is how to setup auto-renewal for SSL certificates. By default, certificates issued by Certbot expire in three months. I will setup a cron job to automatically run daily and check for certificates about to expire, or that have been compromised and automatically renew them.

First, run `sudo yum install cronie`. This will enable cron for Amazon Linux 2023 which will also enable the `crontab` and `crond` commands. Next, use `crontab -e` to open the cron job file, and add the line shown below, then save and exit. *This will be a test to make sure cron is running properly.*

```plaintext
* * * * * /usr/bin/uptime > /tmp/uptime
```

After about a minute run `cat /tmp/uptime`. If the file was created, then we know cron is running properly.

Now that cron is working, I will implement the cron job recommended by AWS for Certbot auto-renewal which is shown below. (Make sure to remove the test cron job.) This job will run the `certbot renew` command every day at 1:39 and 13:39 as root. The `--no-self-upgrade` flag ensures that Certbot doesn’t auto upgrade itself in the process.

```plaintext
39      1,13    *       *       *       root    certbot renew --no-self-upgrade
```

# **Conclusion**

The main goal of this article was to give the reader an actionable introduction to Nginx, where they can go and immediately apply something they learned. Wether you are just playing around with Nginx for the first time, or trying to optimize your SSL certificate renewal workflow, I hope you learned something from this article.

As always, if there are any questions or comments, please leave a reply. I primarily write these articles to teach myself, so if theres anything that is incorrect please let me know. Thanks for reading!