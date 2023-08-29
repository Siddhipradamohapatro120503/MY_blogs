---
title: "Deploying a Microservice Application"
datePublished: Tue Aug 29 2023 04:21:29 GMT+0000 (Coordinated Universal Time)
cuid: cllvswv5i00010al4asnx3x2g
slug: deploying-a-microservice-application
tags: docker, kubernetes, wemakedevs, trainwithshubham, tws

---

# Getting Started:

## Installation of Kubeadm on machine

### Both the Master and Worker Nodes

Run the following commands on the master and worker nodes to prepare them for Kubeadm.

```bash
# using 'sudo su' is not a good practice.
sudo apt update
sudo apt-get install -y apt-transport-https ca-certificates curl
sudo apt install docker.io -y

sudo systemctl enable --now docker # enable and start in single command.

# Adding GPG keys.
curl -fsSL "https://packages.cloud.google.com/apt/doc/apt-key.gpg" | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/kubernetes-archive-keyring.gpg

# Add the repository to the sourcelist.
echo 'deb https://packages.cloud.google.com/apt kubernetes-xenial main' | sudo tee /etc/apt/sources.list.d/kubernetes.list

sudo apt update 
sudo apt install kubeadm=1.20.0-00 kubectl=1.20.0-00 kubelet=1.20.0-00 -y
```

### Master Node

1. Initialize the Kubernetes master node.
    
    ```bash
    sudo kubeadm init
    ```
    
    [![image](https://user-images.githubusercontent.com/40052830/261847539-4fed3d68-eb41-423d-b83f-35c3cc11476e.png align="left")](https://user-images.githubusercontent.com/40052830/261847539-4fed3d68-eb41-423d-b83f-35c3cc11476e.png)
    
    After successfully running, your Kubernetes control plane will be initialized successfully.
    
    [![image](https://user-images.githubusercontent.com/40052830/261847658-760276f4-9146-4bc1-aa92-48cc1c0b13f4.png align="left")](https://user-images.githubusercontent.com/40052830/261847658-760276f4-9146-4bc1-aa92-48cc1c0b13f4.png)
    
2. Set up local kubeconfig (both for the root user and the average user):
    
    ```bash
    mkdir -p $HOME/.kube
    sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
    sudo chown $(id -u):$(id -g) $HOME/.kube/config
    ```
    
    [![image](https://user-images.githubusercontent.com/40052830/261847772-f647adc1-0976-490e-b9c9-f6f96908d6fe.png align="left")](https://user-images.githubusercontent.com/40052830/261847772-f647adc1-0976-490e-b9c9-f6f96908d6fe.png)
    
3. Apply Weave Network:
    
    ```bash
    kubectl apply -f https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml
    ```
    
    [![image](https://user-images.githubusercontent.com/40052830/261847852-ec7b4684-7719-4d09-81d8-eee27b98972a.png align="left")](https://user-images.githubusercontent.com/40052830/261847852-ec7b4684-7719-4d09-81d8-eee27b98972a.png)
    
4. Generate a token for worker nodes to join:
    
    ```bash
    sudo kubeadm token create --print-join-command
    ```
    
    [![image](https://user-images.githubusercontent.com/40052830/261848054-0370839b-bbac-415c-9d5a-9ab52cd3108b.png align="left")](https://user-images.githubusercontent.com/40052830/261848054-0370839b-bbac-415c-9d5a-9ab52cd3108b.png)
    
5. Expose port 6443 in the Security group for the Worker to connect to the master node.
    

[![image](https://user-images.githubusercontent.com/40052830/261848106-b3f5df01-acb0-419f-aa70-6d51819f4ec0.png align="left")](https://user-images.githubusercontent.com/40052830/261848106-b3f5df01-acb0-419f-aa70-6d51819f4ec0.png)

## Deploying Microservice application on Kubernetes

We will clone the repo of one **Flask Application** to Deploy

```bash
git clone https://github.com/LondheShubham153/microservices-k8s.git
```

Then we will move to That directory, where the **manifest file** will be present.

```bash
cd microservices-k8s/flask-api/k8s/
```

First, we will start with the **Mongo deployment** installation

```bash
 kubectl apply -f mongo-pv

 kubectl apply -f mongo-pvc.yml

kubectl apply -f mongo.yml
```

Then we Install our main **application deployment** file

```bash
kubectl apply -f taskmaster.yml

kubectl apply -f taskmaster-svc.yml
```

We list the number of **pods** we have created

```bash
 kubectl get pods
```

```bash
NAME                          READY   STATUS    RESTARTS   AGE
mongo-6879558ffc-mr4rz        1/1     Running   0          7m32s
taskmaster-74fd98cbd6-d8dfk   1/1     Running   0          3m12s
```

Then will Check using the **Curl command**

```bash
curl http://127.0.0.1:30007
```

The results show this:

```bash
{"message":"Welcome to Tasks app! I am running inside taskmaster-74fd98cbd6-d8dfk pod!"}
```

If you want to add more tasks, use this command:

```bash
{"message":"Welcome to Tasks app! I am running inside taskmaster-74fd98cbd6-d8dfk pod!"}
```

Thank you for reading my blog. Subscribe to my newsletter for the upcoming Wonderful Blogs.