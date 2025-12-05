---
title : "Setup EventBridge Rule"
date: "2025-09-09"
weight : 7
chapter : false
pre : " <b> 5.7. </b> "
---

#### Setup EventBridge Rule

This step connects the Alarm with the Reboot action through Systems Manager.

#### Steps

1. **Access Amazon EventBridge Console**
   - Open AWS Management Console and select EventBridge service.

2. **Create a new Rule**
   - Select **Rules** -> **Create rule**
   - Name: **Rule-Reboot-On-High-Memory**
   - Select **Rule with an event pattern**

3. **Configure Events (Step 4a: Triggering Events)**
   - Click on the **Triggering Events** block (Left block)
   - In the **Event pattern** section below:
     - **Source**: AWS services
     - **Service**: CloudWatch
     - **Event type**: CloudWatch Alarm State Change
     - **Specific alarm name(s)**: Select **High-Memory-Auto-Reboot**
     - **Specific state(s)**: Select **ALARM**

4. **Configure Targets (Step 4b: Targets)**
   - Click on the **Target 1** block (Right block)
   - In the **Target settings** section below:
     - **Target types**: AWS service
     - **Select a target**: Systems Manager Automation
     - **Document**: Find and select **AWS-RestartEC2Instance**
     - **InstanceId**: Enter the ID of **Web-Server-Test** (example: `i-0xxxx...`)
     - **Execution role**: Select **Create a new role for this specific resource**

5. **Finish**
   - Click **Create rule** to complete

You have successfully set up an EventBridge Rule to automatically restart the EC2 instance when RAM exceeds 80%.