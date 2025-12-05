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

2. **Create a new Role**
   - Select **Roles** from the left menu.
   - Click **Create role**.

3. **Configure Trusted Entity Type**
   - Under **Trusted entity type**, select **AWS service**.
   - Under **Service or use case**, select **EC2**.
   - Click **Next**.

4. **Attach Permissions Policies**
   - In the **Permissions policies** search box, find and select (check the box) 2 permissions:
     - **CloudWatchAgentServerPolicy** (To push logs/metrics)
     - **AmazonSSMManagedInstanceCore** (To connect Session Manager and execute Automation)
   - Click **Next**.

5. **Name the Role**
   - Set the Role name as: **EC2-Monitor-AutoFix-Role**
   - Click **Create role**.

You have successfully created an IAM Role to grant permissions to the EC2 instance.