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

![console](/images/5-Workshop/5.7-eventbridge-rule/console.png)

2. **Create a new Rule**
   - Select **Rule with an event pattern**
   - Select **Rules** -> **Create rule**

![get started](/images/5-Workshop/5.7-eventbridge-rule/get-started.png)

3. **Configure Events (Step 4a: Triggering Events)**
   - In the Event section on the left, select **AWS SERVICE EVENT**
   - Search event: **CloudWatch Alarm State Change**
   - Drag and drop into the **Triggering Event** box

![trggering event](/images/5-Workshop/5.7-eventbridge-rule/triggering-event.png)

4. **Configure Targets (Step 4b: Targets)**
   - On the left section, select the **Targets** section
   - Search target: **EC2 Reboot Instance**
   - Drag and drop into the **Targets** box
   - In the Target configuration section, assign the EC2 instance ID that you created in the previous steps
   - Select **Create a new role for this specific resource**

![target](/images/5-Workshop/5.7-eventbridge-rule/target.png)

![target2](/images/5-Workshop/5.7-eventbridge-rule/target-2.png)

5. **Finish**
   - Click **Create rule** to complete
   - Name: **Rule-Reboot-On-High-Memory**

![finish](/images/5-Workshop/5.7-eventbridge-rule/finish.png)

You have successfully set up an EventBridge Rule to automatically restart the EC2 instance when RAM exceeds 50%.