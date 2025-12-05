---
title : "Create IAM Role"
date: "2025-09-09"
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### Create IAM Role

First, we need to grant permissions to the EC2 Instance so it can send data to CloudWatch and allow Systems Manager to control it (for reboot).

#### Steps

1. **Access IAM Console**
   - Open AWS Management Console and select IAM service.

![console](/images/5-Workshop/5.3-iam/console.png)

2. **Create a new Role**
   - Select **Roles** from the left menu.
   - Click **Create role**.

![iam console](/images/5-Workshop/5.3-iam/iam-console.png)

3. **Configure Trusted Entity Type**
   - Under **Trusted entity type**, select **AWS service**.
   - Under **Service or use case**, select **EC2**.
   - Click **Next**.

![trusted entity](/images/5-Workshop/5.3-iam/trusted-entity.png)

4. **Attach Permissions Policies**
   - In the **Permissions policies** search box, find and select (check the box) 2 permissions:
     - **CloudWatchAgentServerPolicy** (To push logs/metrics)
     - **AmazonSSMManagedInstanceCore** (To connect Session Manager and execute Automation)
   - Click **Next**.

![per1](/images/5-Workshop/5.3-iam/per1.png)

![per2](/images/5-Workshop/5.3-iam/per2.png)

5. **Name the Role**
   - Set the Role name as: **EC2-Monitor-AutoFix-Role**
   - Click **Create role**.

![name](/images/5-Workshop/5.3-iam/name.png)

You have successfully created an IAM Role to grant permissions to the EC2 instance.