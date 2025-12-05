---
title : "Launch EC2 Instance"
date: "2025-09-09"
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

#### Launch EC2 Instance

We will create a server that simulates a web application and pre-install necessary tools.

#### Steps

1. **Access EC2 Console**
   - Open AWS Management Console and select EC2 service.
   - Select **Launch instances**.

![console](/images/5-Workshop/5.4-ec2/console.png)

2. **Configure Instance Details**
   - **Name**: Set as **Web-Server-Test**
   - **OS Images**: Select **Amazon Linux 2023 AMI**
   - **Instance type**: Select **t2.micro** or **t3.micro**
   - **Key pair**: Select **"Proceed without a key pair"** (We will use Session Manager, no need for SSH Key)

![launch1](/images/5-Workshop/5.4-ec2/launch1.png)

![launch2](/images/5-Workshop/5.4-ec2/launch2.png)

3. **Configure Network Settings**
   - Leave as default (ensure it's in Public Subnet with Public IP)

4. **Configure Advanced details**
   - **IAM instance profile**: Select **EC2-Monitor-AutoFix-Role** created in step 1

![launch3](/images/5-Workshop/5.4-ec2/launch3.png)

5. **Configure User Data**
   - Expand the **Advanced details** section
   - Copy and paste the following script into the **User Data** field to automatically install Agent and testing tools:

```bash
#!/bin/bash
dnf update -y
dnf install amazon-cloudwatch-agent stress -y
```

6. **Launch Instance**
    - Click **Launch instance**
    - Wait a few minutes for the Instance to transition to **Running** state