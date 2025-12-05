---
title: "Workshop"
date: "2025-09-09"
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Giám sát CloudWatch và Tự động Khắc phục Sự cố

#### Tổng quan

Trong bài lab này, chúng ta sẽ xây dựng một hệ thống giám sát và tự động khắc phục sự cố sử dụng **AWS CloudWatch**, **EventBridge**, và **Systems Manager**. Hệ thống này sẽ tự động giám sát mức sử dụng bộ nhớ (RAM) của EC2 instance và tự động khởi động lại máy chủ khi bộ nhớ vượt quá ngưỡng 80%.

#### Lợi ích của hệ thống này

- **Giám sát liên tục**: CloudWatch Agent thu thập chỉ số bộ nhớ mỗi 60 giây
- **Cảnh báo tức thời**: SNS Topic gửi thông báo qua email khi Alarm được kích hoạt
- **Tự động khắc phục**: EventBridge Rule kích hoạt Systems Manager để tự động khởi động lại instance
- **Không cần can thiệp thủ công**: Hệ thống hoạt động 24/7 mà không cần sự can thiệp của người dùng

#### Nội dung

1. [Tổng quan về workshop](5.1-Workshop-overview/)
2. [Chuẩn bị](5.2-Prerequiste/)
3. [Tạo IAM Role](5.3-iam/)
4. [Khởi tạo EC2 Instance](5.4-ec2/)
5. [Cấu hình CloudWatch Agent](5.5-cloudwatch-agent/)
6. [Tạo CloudWatch Alarm](5.6-cloudwatch-alarm/)
7. [Thiết lập EventBridge Rule](5.7-eventbridge-rule/)
8. [Kiểm tra (Chaos Testing)](5.8-test/)
9. [Dọn dẹp tài nguyên](5.9-clean-material/)