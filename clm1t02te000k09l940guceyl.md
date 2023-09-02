---
title: "Deployed a Reddit Copy on Kubernetes with Ingress Enabled"
datePublished: Sat Sep 02 2023 09:10:36 GMT+0000 (Coordinated Universal Time)
cuid: clm1t02te000k09l940guceyl
slug: deployed-a-reddit-copy-on-kubernetes-with-ingress-enabled
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693501897093/07045746-9047-40cc-95c6-33563122ac05.png
tags: kubernetes, 90daysofdevops, wemakedevs, trainwithshubham, tws

---

# **Step 1: Clone the source code**

The first step is to clone the source code for the app. You can do this by using this command:`git clone` [`https://github.com/LondheShubham153/reddit-clone-k8s-ingress.git`](https://github.com/LondheShubham153/reddit-clone-k8s-ingress.git)

# Step 2: Containerize the Application using Docker

* Write a Dockerfile with the following code:
    

```bash

FROM node:19-alpine3.15

WORKDIR /reddit-clone

COPY . /reddit-clone

RUN npm install 

EXPOSE 3000

CMD ["npm","run","dev"]
```

# Step 3) Building Docker-Image

Now it's time to build a Docker Image from this Dockerfile. `docker build -t <DockerHub_Username>/<Imagename> .` use this command to build a Docker image.

# Step 4) Push the Image To DockerHub

Now push this Docker Image to DockerHub so our Deployment file can pull this image & run the app in Kubernetes pods.

* First login to your DockerHub account using Command i.e. `docker login` and give your username & password.
    
* Then used `docker push <DockerHub_Username>/<Imagename>` for pushing to the Docker Hub.
    
* You can use an existing Docker image, i.e., ***siddhi2003/reddit-clone,*** for deployment.
    

# Step 5) Write a Kubernetes Manifest File

Now, You might be wondering what this manifest file in Kubernetes is. Don't worry, I'll tell you in brief.

When you are going to deploy to Kubernetes or create Kubernetes resources like a pod, replica-set, config map, secret, deployment, etc., you need to write a file called manifest that describes that object and its attributes either in YAML or JSON. Just like you do in the Ansible playbook.

Of course, you can create those objects by using just the command line, but the recommended way is to write a file so that you can version control it and use it in a repeatable way.

## Write Deployment.yml file

Let's Create a Deployment File For our Application. Use the following code for the ***Deployment.yml*** file.

```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  name: reddit-clone-deployment
  labels:
    app: reddit-clone
spec:
  replicas: 2
  selector:
    matchLabels:
      app: reddit-clone
  template:
    metadata:
      labels:
        app: reddit-clone
    spec:
      containers:
      - name: reddit-clone
        image: siddhi2003/reddit-clone
        ports:
        - containerPort: 3000
```

## Write Service.yml file

```bash
apiVersion: v1
kind: Service
metadata:
  name: reddit-clone-service
  labels:
    app: reddit-clone
spec:
  type: NodePort
  ports:
  - port: 3000
    targetPort: 3000
    nodePort: 31000
  selector:
    app: reddit-clone
```

# Step 5) Deploy the app to Kubernetes and create a Service For It

Now, we have a deployment file for our app and we have a running Kubernetes cluster, We can deploy the app to Kubernetes. To deploy the app you need to run following the command: `kubectl apply -f Deployment.yml` Just Like this create a Service using `kubectl apply -f Service.yml`

If You want to check your deployment and service use the command `kubectl get deployment` & `kubectl get services`

# Step 6) Let's Configure Ingress

## Ingress:

Kubernetes Ingress is an API object and a resource that manages external access to services within a Kubernetes cluster. It provides a way to configure the rules for routing external traffic to services running inside the cluster. Ingress acts as a layer 7 (application layer) HTTP and HTTPS load balancer, enabling you to define how incoming requests to specific hostnames or paths should be directed to different services or pods.

1. **IP Addresses in Kubernetes:** Pods and services in Kubernetes each have their own IP addresses. However, these IPs are not typically exposed to the external internet directly.
    
2. **Node IP and Port Conflicts:** While it's possible to configure a service with a node IP, it's important to note that port numbers for services on the same node cannot be duplicated. This can make it complex to manage which port is associated with which service.
    
3. **Dynamic Nature of Nodes:** Nodes in a Kubernetes cluster can come and go as they are added or removed. Therefore, it's not practical to rely on static node IPs for external services.
    
4. **Ingress Controller:** Ingress is introduced as a solution to handle inbound connections and route external traffic to Kubernetes cluster services. Ingress operates at the application layer (L7) and can allocate and forward ports on each virtual machine (VM) to the service port.
    
5. **Defining Ingress Rules:** Users define a set of rules for Ingress, specifying how external traffic should be directed to various Kubernetes endpoints based on different URLs. These rules are then posted as a source type "ingress" to the Kubernetes API server.
    
6. **Ingress Controller's Role:** When incoming traffic arrives, the Ingress controller takes on the responsibility of fulfilling and routing traffic based on the defined Ingress rules.
    

![](https://matthewpalmer.net/kubernetes-app-developer/articles/ingress.png align="left")

Let's write ingress.yml and put the following code in it:

```bash
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: ingress-reddit-app
spec:
  rules:
  - host: "domain.com"
    http:
      paths:
      - pathType: Prefix
        path: "/test"
        backend:
          service:
            name: reddit-clone-service
            port:
              number: 3000
  - host: "*.domain.com"
    http:
      paths:
      - pathType: Prefix
        path: "/test"
        backend:
          service:
            name: reddit-clone-service
            port:
              number: 3000
```

Minikube doesn't enable ingress by default; we have to enable it first using `minikube addons enable ingress` command.

* If you want to check the current setting for addons in minikube use `minikube addons list` command.
    

Now you can able to create ingress for your service. `kubectl apply -f ingress.yml` use this command to apply ingress settings.

* Verify that the ingress resource is running correctly by using `kubectl get ingress ingress-reddit-app` command.
    

# Step 8) Expose the app

1. First We need to expose our deployment so use `kubectl expose deployment reddit-clone-deployment --type=NodePort` command.
    
2. You can test your deployment using curl -L [**http://192.168.49.2:31000**](http://192.168.49.2:31000). **192.168.49.2** is a minikube ip & Port **31000** is defined in Service.yml
    
3. Then We have to expose our app service `kubectl port-forward svc/reddit-clone-service 3000:3000 --address 0.0.0.0 &`
    

# Test Ingress

Now It's time to test your ingress so use the ***curl -L domain/test*** command in the terminal.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677665654407/76061aa0-1d26-4f2d-9000-447936ca5181.png?auto=compress,format&format=webp align="left")

You can also see the deployed application on **Ec2\_ip:3000**

***Note:- Make sure you open the 3000 port in a security group of your Ec2 Instance.***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677780495226/7ba8afd2-e45e-455c-9b18-ee0a91d8c5a1.png?auto=compress,format&format=webp align="left")

Thank You Shubham Sir for this wonderful project

I hope you like this blog Do check out my other blog for inciteful knowledge hope you like also for more such content subscribe to me newsletter