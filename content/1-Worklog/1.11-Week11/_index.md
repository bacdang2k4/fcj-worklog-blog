---
title: "Week 11 Worklog"
date: "2025-09-09"
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:

* Build AWS infrastructure using Terraform.
* Set up GitHub Actions for automated deployment.
* Complete the CI/CD pipeline for the backend.
* Ensure security and organize infrastructure according to the project architecture

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Analyze system architecture and identify AWS resources to deploy                                                                                                   | 08/11/2025 | 08/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Write Terraform scripts for core services: S3, DynamoDB, IAM                                             | 08/12/2025 | 08/12/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Deploy IoT Core, Lambda, and API Gateway using Terraform | 08/13/2025 | 08/13/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Configure Terraform backend                            | 08/14/2025 | 08/15/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Set up GitHub Actions for Terraform plan / apply                                                                                     | 08/15/2025 | 08/15/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Week 11 Achievements:

* Complete AWS infrastructure using Terraform.
* Successfully deployed important services:
  - AWS IoT Core
  - Lambda
  - API Gateway
  - DynamoDB
  - IAM
* Configure Terraform remote state using S3 and lock using DynamoDB.
* Build automated GitHub Actions pipeline:
  - Run `terraform init`
  - `terraform plan`
  - `terraform apply`
* Pipeline works stably, can be redeployed many times without errors.
* Infrastructure closely follows the project architecture diagram.