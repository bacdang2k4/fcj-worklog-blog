---
title: "Week 7 Worklog"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---
### **Week 7 Objectives:**

*   Learn about AWS Lambda.
*   Learn about the AWS CLI and how to deploy a Java function to Lambda using the AWS CLI.
*   Understand how API Gateway and Lambda work together.
1
### Tasks to be implemented this week:
| Day | Task | Start Date | Completion Date | Resources |
| :-- | :--- | :--- | :--- | :--- |
| Mon | - Get an overview of AWS Lambda: concepts, architecture, advantages of the serverless model, and how Lambda executes code. | 20/10/2025 | 20/10/2025 | https://cloudjourney.awsstudygroup.com/ |
| Tue | - Study the AWS CLI: its functions, how to install and configure access to an AWS account using an IAM User; learn the syntax of basic commands. | 21/10/2025 | 21/10/2025 | https://cloudjourney.awsstudygroup.com/ |
| Wed | - Practice installing the AWS CLI on a personal machine, configuring credentials, and testing some resource management commands (S3, EC2, Lambda). | 22/10/2025 | 22/10/2025 | https://cloudjourney.awsstudygroup.com/ |
| Thu | - Learn the process of deploying a Java Function to AWS Lambda: preparing a Maven project, packaging a .jar file, creating and uploading the function using the AWS CLI. | 23/10/2025 | 23/10/2025 | https://cloudjourney.awsstudygroup.com/ |
| Fri | - Practice deploying a Java Function to Lambda using the AWS CLI, assigning the appropriate IAM role, and testing the function's operation. | 24/10/2025 | 24/10/2025 | https://cloudjourney.awsstudygroup.com/ |
| Sat | - Understand how API Gateway connects with AWS Lambda to build a backend API; configure endpoints and test API calls. | 25/10/2025 | 25/10/2025 | https://cloudjourney.awsstudygroup.com/ |
| Sun | - Consolidate learned knowledge: the relationship between Lambda – API Gateway – AWS CLI, document the deployment process, and prepare the weekly report. - Write the **work log for week 6**. | 26/10/2025 | 26/10/2025 | https://cloudjourney.awsstudygroup.com/ |


### **Week 7 Achievements:**

#### 1. Clear Understanding of AWS Lambda
-   Grasped the concept and role of **AWS Lambda** in the *serverless* model.
-   Understood Lambda's operational mechanism: the trigger process, function execution, and returning results.
-   Distinguished the differences between **Lambda** and **EC2** regarding:
    -   Infrastructure Management
    -   Usage Costs
    -   Scalability and Flexibility.

#### 2. Proficiency in Using the AWS CLI
-   Successfully installed and configured the **AWS CLI** on a personal machine using an IAM User.
-   Practiced basic commands:
    -   Listing S3 buckets.
    -   Creating and viewing information for a Lambda function.
    -   Managing basic resources on AWS.
-   Understood how the AWS CLI sends API requests and the authentication mechanism using Access Key/Secret Key.

#### 3. Practical Experience Deploying a Java Function to AWS Lambda via AWS CLI
-   Built a Java project using **Maven**, created a handler class, and packaged it into a .jar file.
-   Used the aws lambda create-function command to upload and deploy the function.
-   Assigned an appropriate **IAM Role** to grant the Lambda function execution permissions.
-   Tested the function's operation with the command:
    