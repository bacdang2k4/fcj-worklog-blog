---
title : "Cleanup Resources"
date: "2025-09-09"
weight : 9
chapter : false
pre : " <b> 5.9. </b> "
---

#### Cleanup Resources

After completing the above steps, you should clean up AWS resources to avoid unnecessary costs.

#### Steps

1. **Delete EventBridge Rule**
   - Access Amazon EventBridge Console
   - Select **Rules**
   - Find and select **Rule-Reboot-On-High-Memory**
   - Click **Delete**

2. **Delete CloudWatch Alarm**
   - Access CloudWatch Console
   - Select **All alarms**
   - Find and select **High-Memory-Auto-Reboot**
   - Click **Delete alarm**

3. **Delete SNS Topic**
   - Access SNS Console
   - Select **Topics**
   - Find and select **Admin-Alerts**
   - Click **Delete**

4. **Delete EC2 Instance**
   - Access EC2 Console
   - Select **Instances**
   - Find and select **Web-Server-Test**
   - Click **Instance State** -> **Terminate**
   - Confirm **Terminate**

5. **Delete IAM Role**
   - Access IAM Console
   - Select **Roles**
   - Find and select **EC2-Monitor-AutoFix-Role**
   - Click **Delete**
   - Confirm **Delete role**

#### Important Notes

- Make sure you no longer need these resources before deleting
- Deletion is permanent and cannot be recovered
- After deletion, you will not be charged for these resources