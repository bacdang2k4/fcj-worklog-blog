---
title : "Introduction"
date: "2025-09-09"
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Introduction to Automated Remediation

+ Automated Remediation is the use of software and logical rules to detect and fix infrastructure issues without human intervention. They are critical components for building "self-healing" systems that minimize service downtime.
+ Computing resources running in production may encounter unexpected issues (such as memory overflow, application crashes). Through the combination of Amazon CloudWatch (monitoring) and AWS Systems Manager (execution), the system can automatically respond to these issues immediately instead of waiting for engineers to handle them manually.

#### Workshop Overview
In this workshop, you will deploy a completely automated monitoring and issue remediation process.
+ **Web-Server-Test** is an EC2 Instance resource that acts as a test application server. A **CloudWatch Agent** has been installed and configured within this instance to collect memory (RAM) metrics – a metric not monitored by default by AWS. You will use the stress tool to simulate a memory overflow attack, causing the server to become unresponsive.
+ **EventBridge & Systems Manager** simulate an automated operations team. A Rule is configured to listen for alerts from CloudWatch. When memory exceeds the safe threshold, the system will automatically trigger a restart command (Reboot) on the instance through Systems Manager Automation. This mechanism simulates rapid service recovery in real-world environments. In this workshop, we perform the Reboot action to see results immediately, but for production workloads, you can configure more complex procedures such as dumping RAM for error analysis before restarting or replacing instances with Auto Scaling.

![overview](/images/5-Workshop/5.1-Workshop-overview/ws.png)
