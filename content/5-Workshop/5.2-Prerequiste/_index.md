---
title : "Preparation Steps"
date: "2025-09-09"
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

#### IAM Permissions
Attach the following IAM permission policy to your AWS user account to deploy and clean up resources in this workshop.
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "WorkshopPermissions",
            "Effect": "Allow",
            "Action": [
                "ec2:RunInstances",
                "ec2:TerminateInstances",
                "ec2:StopInstances",
                "ec2:StartInstances",
                "ec2:Describe*",
                "ec2:CreateTags",
                "ec2:RebootInstances",
                "iam:CreateRole",
                "iam:AttachRolePolicy",
                "iam:PassRole",
                "iam:PutRolePolicy",
                "iam:GetRole",
                "iam:ListRoles",
                "iam:CreatePolicy",
                "cloudwatch:PutMetricData",
                "cloudwatch:GetMetricStatistics",
                "cloudwatch:ListMetrics",
                "cloudwatch:PutMetricAlarm",
                "cloudwatch:DeleteAlarms",
                "cloudwatch:DescribeAlarms",
                "events:PutRule",
                "events:PutTargets",
                "events:DeleteRule",
                "events:RemoveTargets",
                "events:DescribeRule",
                "events:ListRules",
                "ssm:GetDocument",
                "ssm:ListDocuments",
                "ssm:DescribeInstanceInformation",
                "ssm:GetAutomationExecution",
                "ssm:StartAutomationExecution",
                "sns:CreateTopic",
                "sns:Subscribe",
                "sns:Publish",
                "sns:DeleteTopic"
            ],
            "Resource": "*"
        }
    ]
}

```


#### Lab Environment

We will build the infrastructure from scratch to understand how to install the Agent and configure permissions (IAM Role).

Basic Requirements:

**Default VPC:** Ensure that your us-east-1 region has a Default VPC available. If you have already deleted it, create a new VPC with a simple Public Subnet configuration.

**Internet Access:** The EC2 Instance in this lab will need Internet connectivity to download the stress package and amazon-cloudwatch-agent.

Check Default VPC in Console

After ensuring the permissions and VPC are in place, you are ready to proceed to the implementation phase.
