---
title: "Workshop"
date: "2025-09-09"
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# CloudWatch Monitoring and Auto-Recovery System

#### Overview

In this lab, you will build a monitoring and auto-recovery system using **AWS CloudWatch**, **EventBridge**, and **Systems Manager**. This system will continuously monitor the RAM usage of an EC2 instance and automatically restart the server when memory exceeds the 80% threshold.

#### Benefits of This System

- **Continuous Monitoring**: CloudWatch Agent collects memory metrics every 60 seconds
- **Real-time Alerts**: SNS Topic sends email notifications when an Alarm is triggered
- **Automatic Recovery**: EventBridge Rule triggers Systems Manager to automatically restart the instance
- **No Manual Intervention**: The system operates 24/7 without user intervention

#### Content

1. [Workshop overview](5.1-Workshop-overview/)
2. [Prerequisite](5.2-Prerequiste/)
3. [Create IAM Role](5.3-iam/)
4. [Launch EC2 Instance](5.4-ec2/)
5. [Configure CloudWatch Agent](5.5-cloudwatch-agent/)
6. [Create CloudWatch Alarm](5.6-cloudwatch-alarm/)
7. [Setup EventBridge Rule](5.7-eventbridge-rule/)
8. [Testing (Chaos Testing)](5.8-test/)
9. [Cleanup Resources](5.9-clean-material/)