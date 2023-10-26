---
title: "Creating an Amazon EC2 instance is a fundamental task when working with Amazon Web Services (AWS)."
datePublished: Thu Oct 26 2023 03:30:10 GMT+0000 (Coordinated Universal Time)
cuid: clo6mma08000009icfm7v28hm
slug: creating-an-amazon-ec2-instance-is-a-fundamental-task-when-working-with-amazon-web-services-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698093620150/8e6671b5-2716-4813-b8c2-446dd43dc51a.png
tags: ec2, aws, cloud-computing, ecs, eks

---

### **Step 1: Log In to the AWS Console**

1. Visit the AWS website: Go to [https://aws.amazon.com/](https://aws.amazon.com/).
    
2. Sign In: If you already have an AWS account, sign in. If not, you can create a new account.
    

### **Step 2: Accessing the EC2 Dashboard**

1. Navigate to EC2: Once you're logged in, click on "Services" at the top left corner of the AWS Management Console.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698091767287/166a130f-4ef1-4e2e-ada8-0df930a3a32a.png align="center")
    
2. Select EC2: Under the "Compute" section, you'll find "EC2." Click on it to enter the EC2 Dashboard.
    

### **Step 3: Launching Your First EC2 Instance**

1. Click "Launch Instance": In the EC2 Dashboard, click the "Launch Instance" button to start the instance creation process.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698091825003/abda517e-2860-48a8-a542-3ac82bf3ccc1.png align="center")
    
2. Choose an Amazon Machine Image (AMI): You'll be presented with a variety of AMIs, including Amazon Linux, Ubuntu, Windows Server, and many more. Select the AMI that best suits your needs. For beginners, Amazon Linux is a good choice.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698091877010/25c7b507-1317-4d1f-a06c-5c4bc06179e9.png align="center")
    
3. Choose an Instance Type: AWS offers a range of instance types with varying CPU, memory, and network capabilities. For your first instance, you can select "t2.micro," as it's part of the free tier and a good starting point for learning.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698091903452/036e3e9d-276e-407f-aed4-228b3dfb69db.png align="center")
    
4. Configure Instance Details: Here, you can specify the number of instances, network settings, and more. For beginners, the default settings will generally suffice.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698091934604/65823d32-58ff-4d90-b651-1e3d01be478a.png align="center")
    
5. Add Storage: You can configure the size and type of the root storage for your instance. The default settings are often sufficient for basic use.
    
6. Add Tags (Optional): You can assign key-value tags to your instance for better organization and management.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698092862669/6e01031e-bdd4-47f0-9fe9-fe0c04700830.png align="center")
    
7. Configure Security Groups: Security groups act as firewalls for your instance, controlling incoming and outgoing traffic. Create a new security group or select an existing one, and configure the rules. Ensure you allow SSH (port 22 for Linux) or RDP (port 3389 for Windows) access for remote connections.
    
8. Review and Launch: Review your instance configuration, and click "Launch" to proceed.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698091999024/12aa5957-0dbe-4445-b303-15b551d39ce8.png align="center")
    
9. Create or Use an Existing Key Pair: To access your instance, you need a key pair. You can choose to create a new one or use an existing key pair. If creating a new key pair, make sure to download and save the private key file (.pem). It's crucial to keep this file safe, as you'll need it to connect to your instance.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698092080054/9699a24b-8948-4bd8-97f6-e0c0171469f8.png align="center")
    

### **Step 4: Connecting to Your EC2 Instance**

First, select The instance and go to connect tab &gt; then SSH Client

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698092158122/19ae62d9-d0d1-4012-9998-d06d1f84ab19.png align="center")

Copy the SSH Example Command And paste it into The CMD of the Downloads Folder To connect because The private key is Present in the Download folder, which is the Pem file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698092405066/f1c3487b-1658-4a71-b250-bddbc3e01ed2.png align="center")

It will ask for permission for Yes, No, or Fingerprint.

Bingo It got connected to your terminal. You can ace it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698092621759/84cf1775-4d0a-4a22-891f-52c0cfb23521.png align="center")

1. Navigate to Instances: In the EC2 Dashboard, under the "Instances" section, you will find the instance you just launched.
    
2. Connect to Your Instance: Select your instance and click "Connect." Follow the provided instructions for connecting to your instance. For Linux instances, you'll use SSH with the private key file (.pem), and for Windows instances, you'll use RDP.
    

😊 Thank you so much for reading my blog! 😊 I hope you found it helpful and informative. If you did, please 👍 give it a like and 💌 subscribe to my newsletter for more of this type of content. 💌

I'm always looking for ways to improve my blog, so please feel free to leave me a comment or suggestion. 💬

Thanks again for your support! 😊