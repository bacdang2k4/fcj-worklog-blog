---
title: "Activities & Deliverables"
date: "2025-09-09"
weight: 3
chapter: false
pre: " <b> 2.3 </b> "
---

# 3. Activities & Deliverables

## 3.1 Activities and Deliverables Matrix

The project is executed over a **12-week timeline** (September - November 2025), with **Week 1-7** focused on AWS fundamentals and preparation, and **Week 8-12** dedicated to hands-on development following Agile methodology.

| Project Phase | Timeline | Key Activities | Deliverables / Milestones | Est. Effort |
| :--- | :--- | :--- | :--- | :--- |
| **I. AWS Fundamentals & Planning** | Week 1-7 | • Learn AWS Core Services<br>• Finalize Architecture & DB Schema<br>• Setup AWS Account & IAM Roles<br>• Initialize Terraform State (S3) | • AWS Certification Knowledge<br>• Architecture Document (LLD)<br>• Terraform Backend Setup<br>• Database Schema Design | 40 man-days |
| **II. Hardware & IoT Integration** | Week 8 | • Wire ESP32 with AS608, MQ-3, MAX30102<br>• Implement MQTT Auth Logic<br>• Setup AWS IoT Core Pipeline<br>• Calibrate Sensors | • Flashed ESP32 Device<br>• IoT Core Connection Established<br>• Sensor Reading Logs | 8 man-days |
| **III. Authentication & Backend** | Week 9 | • Develop Lambda Functions (Python)<br>• Configure API Gateway & Rules Engine<br>• Implement Hybrid Auth System | • Deployed Serverless Stack<br>• Working REST APIs<br>• Fingerprint Authentication | 8 man-days |
| **IV. Frontend Development** | Week 10 | • Build Web Portal (HTML/CSS/JS)<br>• Integrate APIs<br>• Setup AWS Amplify Hosting | • Public Website URL<br>• Dashboard UI<br>• Citizen Lookup Feature | 8 man-days |
| **V. Infrastructure as Code & CI/CD** | Week 11 | • Implement Terraform for IaC<br>• Setup GitHub Actions workflow<br>• Configure AWS WAF Rules<br>• Security Hardening | • Automated CI/CD Pipeline<br>• WAF Protection Active<br>• CloudWatch Monitoring | 8 man-days |
| **VI. Testing & Documentation** | Week 12 | • End-to-End System Testing<br>• Final Demo to Stakeholders<br>• Documentation & Knowledge Transfer | • Final Project Report<br>• Source Code Repository<br>• User Manual | 8 man-days |

---

## 3.2 Out of Scope

The following items are explicitly **excluded** from this Proof of Concept (PoC) to ensure focused delivery within the 12-week timeframe:

* **Mobile Application:** No native iOS or Android apps will be developed; the mobile-responsive Web Portal will serve mobile users.
* **Industrial Hardware Design:** The prototype will use breadboards or a basic 3D-printed case, not an IP67-rated industrial enclosure.
* **Legal Admissibility:** The alcohol sensor readings are for technical demonstration only and are not certified for legal enforcement in court.
* **Legacy Integration:** No integration with existing on-premise government SQL servers or legacy police databases.

---

## 3.3 Path to Production

The current system represents a **Technical Proof of Concept (PoC)**. To transition this solution to a Production-ready environment for real-world deployment, the following steps are required:

1.  **High Availability:**
    * Enable **DynamoDB Global Tables** for multi-region redundancy.
    * Deploy API Gateway across multiple Availability Zones (AZs).
2.  **Offline Resilience:**
    * Implement **AWS IoT Greengrass** on a local gateway to buffer violation data when network connectivity is lost.
3.  **Security Hardening:**
    * Migrate hardcoded configuration secrets to **AWS Secrets Manager**.
    * Conduct rigorous 3rd-party Penetration Testing.
4.  **Operational Excellence:**
    * Set up advanced **CloudWatch Anomaly Detection** alerts.
    * Establish a formal **Incident Response Plan**.