---
title : "Tạo IAM Role"
date: "2025-09-09"
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### Tạo IAM Role

Trước tiên, chúng ta cần cấp quyền cho EC2 Instance để nó có thể gửi dữ liệu lên CloudWatch và cho phép Systems Manager điều khiển (để reboot).

#### Các bước thực hiện

1. **Truy cập IAM Console**
   - Mở AWS Management Console và chọn IAM service.

![console](/images/5-Workshop/5.3-iam/console.png)

2. **Tạo Role mới**
   - Chọn **Roles** ở menu bên trái.
   - Nhấn **Create role**.

![iam console](/images/5-Workshop/5.3-iam/iam-console.png)

3. **Cấu hình Trusted Entity Type**
   - Tại mục **Trusted entity type**, chọn **AWS service**.
   - Tại mục **Service or use case**, chọn **EC2**.
   - Nhấn **Next**.

![trusted entity](/images/5-Workshop/5.3-iam/trusted-entity.png)

4. **Gán Permissions Policies**
   - Tại ô tìm kiếm **Permissions policies**, tìm và chọn (tích vào ô vuông) 2 quyền sau:
     - **CloudWatchAgentServerPolicy** (Để đẩy logs/metrics)
     - **AmazonSSMManagedInstanceCore** (Để kết nối Session Manager và thực thi Automation)
   - Nhấn **Next**.

![per1](/images/5-Workshop/5.3-iam/per1.png)

![per2](/images/5-Workshop/5.3-iam/per2.png)

5. **Đặt tên Role**
   - Đặt tên Role là: **EC2-Monitor-AutoFix-Role**
   - Nhấn **Create role**.

![name](/images/5-Workshop/5.3-iam/name.png)

Bạn đã tạo thành công IAM Role để cấp quyền cho EC2 instance.