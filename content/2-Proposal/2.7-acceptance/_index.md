---
title: "Acceptance"
date: "2025-09-09"
weight: 7
chapter: false
pre: " <b> 2.7 </b> "
---

# 7. Acceptance

## 7.1 Acceptance Process

To conclude the project, the acceptance process will follow these simple steps:

1.  **Submission:** Team SPICA submits the **Source Code**, **Deployment Scripts (Terraform)**, and **Final Report** to the Instructor/Customer.
2.  **Review Period:** The Customer has **5 business days** to test and verify the system.
3.  **Sign-off:** If all criteria below are met, the Customer signs the **Project Acceptance Form**.

---

## 7.2 Acceptance Criteria

The project is considered complete when the following 3 conditions are met:

1.  **Functional Edge Device:**
    * The ESP32 successfully unlocks **only** when a registered fingerprint is scanned.
    * The device sends alcohol and health data to AWS immediately after measurement.

2.  **Working Web Portal:**
    * Violation records appear on the public website within **5 seconds** of recording.
    * Users can successfully search for violations using a valid ID (CCCD).

3.  **Deployable Code:**
    * The backend infrastructure can be re-created automatically using the provided **Terraform** scripts without errors.

---

## 7.3 Rejection & Fixes

* If any bug is found (e.g., device fails to connect, website crashes), the Customer must notify Team SPICA within the review period.
* The team has **3 business days** to fix the issue and resubmit for approval.