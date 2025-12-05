---
title : "Configure CloudWatch Agent"
date: "2025-09-09"
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

#### Configure CloudWatch Agent

By default, EC2 does not monitor RAM (Memory) metrics. We need to configure the Agent to collect this metric.

#### Steps

1. **Access EC2 Instance via Session Manager**
   - In the EC2 instance list, select **Web-Server-Test**
   - Click **Connect**
   - Select the **Session Manager** tab
   - Click **Connect** to open the command-line interface

![connect1](/images/5-Workshop/5.5-cloudwatch-agent/connect1.png)

![connect2](/images/5-Workshop/5.5-cloudwatch-agent/connect2.png)

2. **Create Agent Configuration File**
   - Create the configuration file using the following command (Copy the entire block and paste into terminal):

```bash
sudo tee /opt/aws/amazon-cloudwatch-agent/bin/config.json <<EOF
{
  "agent": {
    "metrics_collection_interval": 60,
    "run_as_user": "root"
  },
  "metrics": {
    "metrics_collected": {
      "mem": {
        "measurement": [
          "mem_used_percent"
        ],
        "metrics_collection_interval": 60
      }
    }
  }
}
EOF
```

3. Start Agent to Load Configuration
  - Run the following command:
```
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -s -c file:/opt/aws/amazon-cloudwatch-agent/bin/config.json
```

You have successfully configured CloudWatch Agent to monitor the memory (RAM) metrics of your EC2 instance.