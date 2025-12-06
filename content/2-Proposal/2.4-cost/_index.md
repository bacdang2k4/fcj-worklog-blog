---
title: "Cost Breakdown"
date: "2025-09-09"
weight: 4
chapter: false
pre: " <b> 2.4 </b> "
---

# 4. Expected Cost Breakdown

## 4.1 AWS Operational Costs (Monthly)

The following cost estimation is based on a **Pilot Phase workload** assumption of approximately **10,000 violation records/month** (equivalent to ~330 inspections/day) in the `ap-southeast-1` (Singapore) or `us-east-1` (N. Virginia) region.

| Service | Estimated Cost (USD) | Notes |
| :--- | :--- | :--- |
| **AWS WAF** | **$6.00** | 1 Web ACL + 1 Rule Group (Essential for API security). |
| **Amazon CloudWatch** | **$2.80** | ~5GB of Log ingestion & storage + 3 Alarm metrics. |
| **AWS Amplify** | **$2.72** | Hosting (with built-in CloudFront CDN), Build minutes (100 mins), and Data Transfer (20GB). |
| **AWS IoT Core** | **$1.00** | Connectivity & Messaging costs for ~10,000 MQTT messages. |
| **AWS Lambda** | **$0.22** | Compute cost for ~25,000 invocations (Includes Free Tier buffer). |
| **Amazon API Gateway** | **$0.07** | REST API calls (~20,000 requests). |
| **Amazon DynamoDB** | **$0.02** | On-demand Read/Write capacity units (Highly efficient). |
| **GitHub Actions** | **$0.00** | Free for public repositories. |
| **TOTAL** | **~$12.83** | **Per Month** |

> **Note:** Actual costs may vary slightly based on data transfer rates and region selection. This estimate does not account for the AWS Free Tier, which may reduce the cost to **<$10/month** for the first 12 months. Amplify hosting includes built-in CloudFront CDN distribution at no additional cost.

---

## 4.2 Hardware Costs (One-Time)

This is the material cost to build one unit of the **Edge Device Prototype**.

| Component | Model | Est. Price (USD) | Purpose |
| :--- | :--- | :--- | :--- |
| **Microcontroller** | ESP32 WROOM-32 | $5.00 | Main processing unit with Wi-Fi/BLE. |
| **Alcohol Sensor** | MQ-3 Module | $3.00 | Detects alcohol concentration in breath. |
| **Biometric Sensor** | AS608 Optical | $12.00 | Fingerprint scanning and verification. |
| **Health Sensor** | MAX30102 | $3.00 | Measures Heart Rate and SpO2. |
| **Display & UI** | LCD 1602 + Keypad | $2.00 | User interaction interface. |
| **Power & Misc** | Battery, Wires, Case | $3.00 | Consumables and 3D printed casing. |
| **TOTAL** | | **~$25.00** | **Per Device** |

---

## 4.3 Cost Optimization Strategy

To ensure the project remains within budget during the scaling phase, Team SPICA will implement:

1.  **DynamoDB On-Demand:** Eliminates costs for idle time; we only pay for actual reads/writes.
2.  **S3 Lifecycle Policies:** Automatically move old build artifacts and logs to S3 Glacier Deep Archive.
3.  **Lambda Power Tuning:** Optimize memory allocation to find the "sweet spot" between cost and performance.
4.  **Budgets & Alarms:** An AWS Budget alert is set at **$15.00** to notify the team via email immediately if costs exceed the threshold.