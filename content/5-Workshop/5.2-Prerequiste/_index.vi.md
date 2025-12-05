---
title : "Các bước chuẩn bị"
date: "2025-09-09"
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

#### IAM permissions
Gắn IAM permission policy sau vào tài khoản aws user của bạn để triển khai và dọn dẹp tài nguyên trong workshop này.
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

#### Môi trường thực hành

Chúng ta sẽ xây dựng cơ sở hạ tầng từ đầu (Build from scratch) để hiểu rõ cách cài đặt Agent và cấu hình quyền hạn (IAM Role).

Yêu cầu cơ bản:

**VPC Mặc định (Default VPC):** Đảm bảo region us-east-1 của bạn có sẵn Default VPC. Nếu bạn đã xóa nó, hãy tạo một VPC mới với cấu hình Public Subnet đơn giản.

**Internet Access:** EC2 Instance trong bài lab sẽ cần kết nối Internet để tải gói cài đặt stress và amazon-cloudwatch-agent.

Kiểm tra Default VPC trong Console

Sau khi đảm bảo các quyền hạn và VPC, bạn đã sẵn sàng bước vào phần triển khai.
