---
title: "Solution Architecture"
date: "2025-12-05"
weight: 2
chapter: false
pre: " <b> 2.2 </b> "
---

# 2. Solution Architecture

## 2.1 High-Level Architecture Diagram
The solution leverages a **Cloud-Native Serverless Architecture** ensuring high scalability, low maintenance, and cost-efficiency. The system connects Edge IoT devices to a centralized AWS backend, protected by comprehensive security layers.

![AWS serverless architecture diagram](/images/2-Proposal/AWS_V13.drawio.png)


**Core Architectural Layers:**
1.  **Edge Layer:** ESP32 microcontrollers interacting with biometric and environmental sensors.
2.  **Ingestion & Compute Layer:** AWS IoT Core for secure messaging and AWS Lambda for serverless business logic.
3.  **Storage Layer:** Amazon DynamoDB for fast, NoSQL data storage of officer registries and violation logs.
4.  **Security & Delivery Layer:** AWS WAF protecting Amplify, and API Gateway for secure backend access.
5.  **DevOps Layer:** Automated CI/CD using **Terraform & GitHub Actions** (Backend) and **AWS Amplify** (Frontend with built-in CloudFront CDN).

---

## 2.2 Technology Stack

The system utilizes the following AWS Services and Hardware components:

| Category | Service / Component | Purpose |
| :--- | :--- | :--- |
| **IoT & Ingestion** | **AWS IoT Core** | Secure MQTT Broker (TLS 1.2) for device communication. |
| **Compute** | **AWS Lambda (Python)** | Serverless functions: `Authorize`, `ProcessViolation`, `GetDashboard`, `SearchByCCCD`. |
| **Database** | **Amazon DynamoDB** | Storage for `DeviceOfficerMap_Pool` and `ViolationsDB` (with Global Secondary Indexes). |
| **API Layer** | **Amazon API Gateway** | Exposes secure REST API endpoints to the frontend. |
| **Security** | **AWS WAF** | Protects Amplify hosting from web exploits. |
| **Frontend** | **AWS Amplify** | Hosting (with built-in CloudFront CDN), CI/CD, and integration for the React/Vue SPA. |
| **Backend DevOps** | **Terraform + GitHub Actions** | Infrastructure as Code deployment and CI/CD automation. |
| **Monitoring** | **Amazon CloudWatch** | System logging, metrics, and error alarming. |

### Edge Hardware Components
* **Controller:** ESP32 (Wi-Fi/Bluetooth enabled).
* **Sensors:**
    * **MQ-3:** Alcohol Concentration detection.
    * **MAX30102:** Heart Rate & SpO2 monitoring (Health safety).
    * **AS608:** Optical Fingerprint Sensor (Biometric Auth).
* **Interface:** 4x4 Matrix Keypad and LCD 1602 Display.

---

## 2.3 Main Processing Flows

### A. Authentication Flow (Hybrid)
1.  **Scan:** Officer places finger on the AS608 sensor.
2.  **Request:** ESP32 sends the encrypted `SlotID` to AWS IoT Core via topic `auth/request`.
3.  **Verify:** IoT Core triggers the `AuthorizeFunction` Lambda.
4.  **Query:** Lambda checks the `DeviceOfficerMap_Pool` table in DynamoDB.
5.  **Response:** System returns an `unlock` or `deny` command. The device activates the MQ-3 sensor only upon success.

### B. Violation Recording Flow
1.  **Measure:** Once unlocked, the device continuously reads MQ-3 sensor data.
2.  **Detect:** If Alcohol Level > Threshold, the device locks and prompts for Citizen ID (CCCD).
3.  **Input:** Officer enters the citizen's CCCD via the Keypad.
4.  **Upload:** Device constructs a JSON payload containing `OfficerID`, `AlcoholLevel`, `Timestamp`, and `CCCD`, sending it to `violations/new`.
5.  **Process:** IoT Core triggers `ProcessViolationFunction` to validate and write the record to `ViolationsDB`.

### C. Public Lookup Flow
1.  **Search:** Citizen enters their National ID (CCCD) on the Web Portal.
2.  **API Call:** The frontend requests `GET /violations?cccd=...` via API Gateway.
3.  **Fetch:** `SearchByCCCDFunction` queries DynamoDB GSIs.
4.  **Display:** Results are returned and displayed on the dashboard in < 1 second.

---

## 2.4 Security Considerations

* **Network Security:** All API endpoints are protected by **AWS WAF** (Web Application Firewall) to block SQL Injection and XSS attacks.
* **Data Encryption:**
    * **In-Transit:** TLS 1.2 for MQTT and HTTPS for API calls.
    * **At-Rest:** DynamoDB tables are encrypted using AWS KMS.
* **Access Control:**
    * **IAM Roles:** Implementation of "Least Privilege" for all Lambda execution roles.
    * **Device Identity:** X.509 Certificates unique to each ESP32 device.
* **Privacy:** Sensitive PII (Citizen ID) is handled securely with strict read access policies.