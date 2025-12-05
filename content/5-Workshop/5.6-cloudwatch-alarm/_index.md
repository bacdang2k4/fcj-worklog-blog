---
title : "Create CloudWatch Alarm"
date: "2025-09-09"
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

#### Create CloudWatch Alarm

We will create an alarm when RAM usage exceeds 80%.

#### Steps

1. **Access CloudWatch Console**
   - Open AWS Management Console and select CloudWatch service.

2. **Create a new Alarm**
   - Select **All alarms** -> **Create alarm**

![console](/images/5-Workshop/5.6-cloudwatch-alarm/console.png)

3. **Select Metric**
   - Click **Select metric**
   - Select **CWAgent** -> **ImageId, InstanceId, InstanceType**
   - Find the **mem_used_percent** metric for the **Web-Server-Test** instance

![select metrics](/images/5-Workshop/5.6-cloudwatch-alarm/select-metric.png)

![select metrics2](/images/5-Workshop/5.6-cloudwatch-alarm/select-metric2.png)

4. **Configure Conditions**
   - **Statistic**: Average
   - **Period**: 1 minute
   - **Threshold type**: Static
   - **Threshold value**: 80 (Greater than 80%)

![condition](/images/5-Workshop/5.6-cloudwatch-alarm/condition.png)

5. **Configure Actions**
   - **Notification**: Select **Create new topic**
   - **Topic name**: Set as **Admin-Alerts**
   - **Email**: Enter your email
   - Click **Create topic**
   - **Important note**: Do not select "EC2 Action" here (because RAM metric is a custom metric and does not support direct reboot). We will use EventBridge instead.
   - Remember to check your email to **Confirm Subscription**.

![action2](/images/5-Workshop/5.6-cloudwatch-alarm/action2.png)

6. **Name the Alarm**
   - **Alarm name**: **High-Memory-Auto-Reboot**
   - Click **Create alarm**

You have successfully created a CloudWatch Alarm to monitor the RAM usage of your EC2 instance.