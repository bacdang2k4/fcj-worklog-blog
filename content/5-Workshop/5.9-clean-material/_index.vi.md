---
title : "Dọn dẹp tài nguyên"
date: "2025-09-09"
weight : 9
chapter : false
pre : " <b> 5.9. </b> "
---

#### Dọn dẹp tài nguyên

Sau khi hoàn thành các bước trên, bạn nên dọn dẹp các tài nguyên AWS để tránh phát sinh chi phí không cần thiết.

#### Các bước thực hiện

1. **Xóa EventBridge Rule**
   - Truy cập Amazon EventBridge Console
   - Chọn **Rules**
   - Tìm và chọn **Rule-Reboot-On-High-Memory**
   - Nhấn **Delete**

2. **Xóa CloudWatch Alarm**
   - Truy cập CloudWatch Console
   - Chọn **All alarms**
   - Tìm và chọn **High-Memory-Auto-Reboot**
   - Nhấn **Delete alarm**

3. **Xóa SNS Topic**
   - Truy cập SNS Console
   - Chọn **Topics**
   - Tìm và chọn **Admin-Alerts**
   - Nhấn **Delete**

4. **Xóa EC2 Instance**
   - Truy cập EC2 Console
   - Chọn **Instances**
   - Tìm và chọn **Web-Server-Test**
   - Nhấn **Instance State** -> **Terminate**
   - Xác nhận **Terminate**

5. **Xóa IAM Role**
   - Truy cập IAM Console
   - Chọn **Roles**
   - Tìm và chọn **EC2-Monitor-AutoFix-Role**
   - Nhấn **Delete**
   - Xác nhận **Delete role**

#### Lưu ý

- Hãy chắc chắn rằng bạn không còn cần các tài nguyên này trước khi xóa
- Việc xóa là vĩnh viễn và không thể phục hồi
- Sau khi xóa, bạn sẽ không bị tính phí cho các tài nguyên này