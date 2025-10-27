---
title: "Proposal"
date: "2025-09-09"
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
# IoT-Based Alcohol Violation Detection System
### A Secure AWS Serverless Solution with Biometric Authentication and DevSecOps

---

## 1. Executive Summary
This project develops a comprehensive **IoT–Cloud platform** to monitor and record alcohol concentration violations.  
The system is composed of two major components:

- **Dedicated Edge Device:** Used by authorized officers, requiring **fingerprint (hybrid) authentication** before operation. The fingerprint SlotID is verified against a **data pool (DynamoDB)** on the cloud to unlock the device.  
- **Public Web Portal:** A web interface that allows anyone to view dashboards and search for their violation history using **National ID (CCCD)**.

The backend is fully **serverless**. The frontend CI/CD workflow is automated using **AWS Amplify**, while backend infrastructure is managed using **Terraform (IaC)** and deployed through **AWS CodePipeline**, following **DevSecOps** best practices.

---

## 2. Context and Solution

### The Problem
The current manual inspection process contains several critical weaknesses in terms of authentication, transparency, and data management.

- **Lack of Accountability**: The system does not have any mechanism to verify the identity of the operating personnel (who conducted the inspection?). This leads to potential misuse of equipment, procedural errors, and a lack of responsibility when incidents or complaints occur.
- **Lack of Transparency**: Citizens who have undergone an inspection have no official, fast, and reliable channel to verify or review their violation records.
- **Fragmented and Unsearchable Data**: Violation data (if recorded) is often stored in scattered logbooks or separate Excel files, without centralized management. This makes it nearly impossible—or extremely time-consuming—to look up a person’s violation history (e.g., by national ID number). As a result, it wastes resources and undermines public trust.
### Proposed Solution
This system provides a secure, transparent, and automated enforcement platform by:

- **Operator Authentication:** Using fingerprint sensors integrated with AWS IoT Core to ensure only authorized personnel can unlock the device.  
- **Auditing:** Every violation is automatically tagged with the operator’s ID for accountability.  
- **Centralized Data Management:** Violation data is transmitted via IoT Core, processed by AWS Lambda, and stored in DynamoDB.  
- **Public Lookup Portal:** A public website built with Amplify + CloudFront, with all API endpoints protected by AWS WAF.  
- **Automated CI/CD Pipelines:**  
  - Frontend CI/CD using Amplify (connected to GitHub).  
  - Backend CI/CD using CodePipeline and Terraform.  

**Key Benefits:**  
- Improved transparency and reduced human error.  
- Fast deployment with low operational cost (~14–16 USD/month).  
- Fully compliant with DevSecOps standards.

---

## 3. Solution Architecture

### AWS Services Used

| Category | Service | Purpose |
|-----------|----------|----------|
| **IoT & Ingestion** | AWS IoT Core | Receive and route data from IoT devices |
| **Compute** | AWS Lambda | 4 functions: Authorize, ProcessViolation, GetDashboard, SearchByCCCD |
| **Database** | Amazon DynamoDB | 2 tables: DeviceOfficerMap_Pool, ViolationsDB (2 GSIs) |
| **API** | Amazon API Gateway | Provide public REST endpoints |
| **Security** | AWS WAF | Protect API and web endpoints |
| **Frontend Hosting** | S3 + CloudFront + Route 53 | Host and distribute the website |
| **Frontend Framework** | AWS Amplify | Automate frontend CI/CD |
| **Backend DevOps** | CodePipeline + CodeBuild + Terraform | Automate IaC deployment |
| **Monitoring** | CloudWatch | System monitoring and alerting |

---

### Hardware Components (Edge)

- **ESP32**, **MQ-3** (Alcohol Sensor)  
- **MAX30102** (Heart Rate / Oxygen Sensor)  
- **AS608** (Fingerprint Sensor)  
- **4x4 Keypad**, **LCD 1602 Display**

![IoT Alcohol Violation Detection System Architecture](/images/2-Proposal/arch.jpeg)

---

### Main Processing Flow

1. **Authentication (Hybrid):**  
   - Officer scans fingerprint → SlotID sent via `auth/request` → IoT Core → Lambda `AuthorizeFunction` → Query DynamoDB → Return `unlock/deny`.  
2. **Violation Recording:**  
   - Once unlocked → Measure alcohol level → If exceeded → Input CCCD → Send `violations/new` → IoT Core → Lambda `ProcessViolationFunction` → Save to DynamoDB.  
3. **Public Web Interface:**  
   - SPA (React/Vue) using Amplify libraries communicates with API Gateway.

---

## 4. Technical Implementation Plan

| Phase | Duration | Key Tasks |
|--------|-----------|-----------|
| **Design & IaC** | Week 1–2 | Finalize architecture, write Terraform scripts |
| **Firmware (ESP32)** | Week 3–4 | Implement authentication and violation reporting |
| **Backend** | Week 5–7 | Develop Lambda functions, IoT Core, and API Gateway |
| **Frontend** | Week 8–9 | Build the web UI with React + Amplify |
| **CI/CD & Security** | Week 10–12 | Configure pipelines, WAF, and CloudWatch monitoring |

---

## 5. Timeline & Milestones

| Month | Phase | Milestone |
|--------|--------|------------|
| **First month** | Design + Firmware | ESP32 authenticates officers and sends sample violations |
| **Second month** | Backend + API | Functional API responding via browser |
| **Third month** | Frontend + CI/CD | Public website live with automated deployment |

---

## 6. Estimated Monthly Budget

| Service | Cost (USD) | Notes |
|----------|-------------|-------|
| AWS WAF | 6.00 | 1 Web ACL + Rule |
| Route 53 | 0.50 | 1 Hosted Zone |
| CodePipeline | 1.00 | Backend pipeline |
| Amplify (Build + Hosting) | 2.72 | 100 build minutes + 20GB transfer |
| CloudWatch | 2.80 | 5GB logs + 3 alarms |
| IoT Core | 1.00 | 10,000 messages |
| CodeBuild | 0.00 | Free tier |
| Lambda | 0.22 | 25,000 invocations |
| API Gateway | 0.07 | 20,000 requests |
| DynamoDB | 0.02 | On-demand capacity |

**Total:** ~14.33 USD/month (~14–16 USD actual cost)

---

## 7. Risk Assessment

| Risk | Impact Level | Likelihood | Mitigation |
|-------|---------------|-------------|-------------|
| **PII Exposure (CCCD)** | Critical | High | Add 2FA or mask last 4 digits of CCCD |
| **Network Disconnection** | High | Medium | ESP32 temporarily stores logs and syncs when online |
| **Sensor Malfunction** | High | Medium | Calibrate periodically, apply signal filtering |
| **CI/CD Failure** | Medium | Medium | Use staging pipeline and code review for IaC |

---

## 8. Expected Outcomes

- **Technical:** Full-stack IoT–Cloud system with biometric authentication, serverless backend, and DevSecOps automation.  
- **Practical:** Improves transparency and accountability of enforcement officers.  
- **Academic:** A graduation project demonstrating mastery of AWS Cloud, IoT, and modern DevOps.

---

