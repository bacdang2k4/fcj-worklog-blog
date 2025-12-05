---
title : "Testing (Chaos Testing)"
date: "2025-09-09"
weight : 8
chapter : false
pre : " <b> 5.8. </b> "
---

#### Testing (Chaos Testing)

Simulate a memory overflow issue to test the system.

#### Steps

1. **Return to the EC2 Session Manager interface**
   - Access EC2 Console
   - Select the **Web-Server-Test** instance
   - Click **Connect**
   - Select the **Session Manager** tab -> **Connect**

2. **Run stress command to push RAM to alarm level**
   - Run the following command (approximately 850MB for t2.micro):

```bash
stress --vm 1 --vm-bytes 850M --vm-hang 300
```

3. Observe the Results

On CloudWatch Alarm:
   - Status changes to red (ALARM)

In Email:
   - Receive alert from SNS

On Session Manager:
   - Connection is disconnected (server is restarting)

On EC2 Console:
   - Instance status changes to Stopping then Running

After Instance restarts:
   - Alarm will automatically return to OK status

#### Conclusion

You have successfully built an automated system for issue recovery! When memory exceeds 80%, the system will automatically:

- Send alert via email
- Trigger EventBridge Rule
- Call Systems Manager to restart the instance
- Instance automatically restarts and returns to OK status