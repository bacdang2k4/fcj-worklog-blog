---
title : "Thiết lập EventBridge Rule"
date: "2025-09-09"
weight : 7
chapter : false
pre : " <b> 5.7. </b> "
---

#### Thiết lập EventBridge Rule

Đây là bước kết nối Alarm với hành động Reboot thông qua Systems Manager.

#### Các bước thực hiện

1. **Truy cập Amazon EventBridge Console**
   - Mở AWS Management Console và chọn EventBridge service.

![console](/images/5-Workshop/5.7-eventbridge-rule/console.png)

2. **Tạo Rule mới**
   - Chọn **Rule with an event pattern**
   - Chọn **Rules** -> **Create rule**
   
   
![get started](/images/5-Workshop/5.7-eventbridge-rule/get-started.png)

3. **Cấu hình Sự kiện (Bước 4a: Triggering Events)**
   - Ở phần Event phía bên trái các bạn chọn **AWS SERVICE EVENT**
   - Search event: **CloudWatch Alarm State Change**
   - Kéo thả vào ô **Triggering Event**

![trggering event](/images/5-Workshop/5.7-eventbridge-rule/triggering-event.png)

4. **Cấu hình Mục tiêu (Bước 4b: Targets)**
   - Ở phần bên trái chọn qua mục **Targets**
   - Search target: **EC2 Reboot Instance**
   - Kéo thả vào ô **Targets**
   - Ở phần Target configuratioon các bạn hãy gán id của ec2 đã tạo ở các bước trước đó
   - Chọn Create a new role for this specific resource
   
![target](/images/5-Workshop/5.7-eventbridge-rule/target.png)

![target2](/images/5-Workshop/5.7-eventbridge-rule/target-2.png)

5. **Hoàn tất**
   - Nhấn **Create rule** để hoàn tất
   - Đặt tên: **Rule-Reboot-On-High-Memory**

![finish](/images/5-Workshop/5.7-eventbridge-rule/finish.png)

Bạn đã thiết lập thành công EventBridge Rule để tự động khởi động lại EC2 instance khi RAM vượt quá 50%.