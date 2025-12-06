---
title: "Background & Motivation"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 2.1 </b> "
---

# 1. Background & Motivation

## 1.1 Executive Summary

### Customer Background
The customer is **FPT University HCMC (Academic Board)** under the mentorship of **Nguyễn Gia Hưng** and potential Traffic Enforcement Agencies. They seek a technological demonstration of how **IoT** and **Cloud Computing** can solve real-world problems in traffic monitoring. The current manual alcohol inspection process suffers from a lack of operator verification, data fragmentation, and low public transparency.

### Business & Technical Objectives
**Team SPICA** proposes a solution named **"IoT-Based Alcohol Violation Detection System"** to modernize this workflow.
The core objectives include:
* **Accountability:** Eliminate unauthorized device usage by enforcing **Biometric Authentication** (Fingerprint) for every session.
* **Transparency:** Empower citizens to verify their own violation records via a secure **Public Web Portal**.
* **Operational Excellence:** Replace manual paperwork with an automated, immutable **Serverless Cloud Database**.

### Key Use Cases
1.  **Secure Device Activation:** Field officers must scan their fingerprint on the **ESP32 Edge Device**. The system authenticates against a central DynamoDB pool via **AWS IoT Core** before enabling the sensors.
2.  **Multi-Sensor Data Collection:** The device captures **Alcohol Concentration (MQ-3)** and **Health Metrics (Heart Rate/SpO2 via MAX30102)** simultaneously to ensure the subject's safety during testing.
3.  **Real-Time Violation Logging:** Violation data is encrypted and synced instantly to AWS, accessible via a Dashboard for admins and a Lookup Portal for citizens.

---

## 1.2 Project Success Criteria

To be considered successful, the system must meet the following quantitative metrics:

| Metric | Target | Notes |
| :--- | :--- | :--- |
| **Authentication Latency** | **< 2 seconds** | Round-trip time from Fingerprint Scan $\to$ Cloud Auth $\to$ Device Unlock. |
| **Data Integrity** | **99.9%** | Zero loss of violation records during network stability tests. |
| **Security Compliance** | **100%** | All Infrastructure-as-Code (Terraform) must pass **tfsec** scans in the CI/CD pipeline. |
| **Deployment Automation** | **Fully Automated** | Backend deploys via **Terraform + GitHub Actions**; Frontend deploys via **AWS Amplify**. |
| **Cost Efficiency** | **<$15 / month** | Operational costs on AWS for the pilot phase. |

---

## 1.3 Assumptions & Constraints

### Hardware & Connectivity
* **Device:** The team has procured the ESP32 WROOM, AS608 (Fingerprint), MQ-3 (Alcohol), and MAX30102 (Pulse Oximeter) sensors.
* **Network:** The Edge Device is assumed to have access to a stable Wi-Fi network or mobile hotspot (4G) during operation.

### Technical Environment
* **Cloud Access:** Team SPICA has Administrator access to a dedicated AWS account for resource provisioning.
* **Development Stack:**
    * **Firmware:** C++ / PlatformIO.
    * **Backend:** Python (Lambda) & Terraform (IaC).
    * **Frontend:** React/Vue.js hosted on S3/Amplify.

### Scope Limitations
* **Legal Admissibility:** This project is a technical Proof of Concept (PoC). The sensor readings are for demonstration purposes and are not legally binding in a real court of law without further industrial calibration.
* **Physical Housing:** The prototype will use a temporary 3D-printed or acrylic case, not an industrial IP67-rated enclosure.