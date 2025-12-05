---
title : "Khởi tạo EC2 Instance"
date: "2025-09-09"
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

#### Khởi tạo EC2 Instance

Chúng ta sẽ tạo máy chủ mô phỏng ứng dụng web và cài đặt sẵn các công cụ cần thiết.

#### Các bước thực hiện

1. **Truy cập EC2 Console**
   - Mở AWS Management Console và chọn EC2 service.
   - Chọn **Launch instances**.

![console](/images/5-Workshop/5.4-ec2/console.png)

2. **Cấu hình Instance Details**
   - **Name**: Đặt là **Web-Server-Test**
   - **OS Images**: Chọn **Amazon Linux 2023 AMI**
   - **Instance type**: Chọn **t2.micro** hoặc **t3.micro**
   - **Key pair**: Chọn **"Proceed without a key pair"** (Chúng ta sẽ dùng Session Manager, không cần SSH Key)

![launch1](/images/5-Workshop/5.4-ec2/launch1.png)

![launch2](/images/5-Workshop/5.4-ec2/launch2.png)

3. **Cấu hình Network Settings**
   - Để mặc định (đảm bảo ở Public Subnet và có Public IP)

4. **Cấu hình Advanced details**
   - **IAM instance profile**: Chọn **EC2-Monitor-AutoFix-Role** vừa tạo ở bước 1

![launch3](/images/5-Workshop/5.4-ec2/launch3.png)

5. **Cấu hình User Data**
   - Mở rộng phần **Advanced details**
   - Sao chép và dán đoạn script sau vào ô **User Data** để tự động cài đặt Agent và công cụ test:

```bash
#!/bin/bash
dnf update -y
dnf install amazon-cloudwatch-agent stress -y 
```

![launch4](/images/5-Workshop/5.4-ec2/launch4.png)

6. **Khởi tạo Instance**
   - Nhấn **Launch instance**
   - Chờ vài phút để Instance chuyển sang trạng thái **Running**

![state](/images/5-Workshop/5.4-ec2/state.png)