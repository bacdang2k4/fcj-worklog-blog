---
title : "Kiểm tra (Chaos Testing)"
date: "2025-09-09"
weight : 8
chapter : false
pre : " <b> 5.8. </b> "
---

#### Kiểm tra (Chaos Testing)

Giả lập sự cố tràn bộ nhớ để kiểm tra hệ thống.

#### Các bước thực hiện

1. **Quay lại giao diện Session Manager của EC2**
   - Truy cập EC2 Console
   - Chọn instance **Web-Server-Test**
   - Nhấn **Connect**
   - Chọn tab **Session Manager** -> **Connect**

2. **Chạy lệnh stress để ép RAM lên mức báo động**
   - Chạy lệnh sau (khoảng 850MB cho t2.micro):

```bash
stress --vm 1 --vm-bytes 850M --vm-hang 300
```

3. Quan sát kết quả

Trên CloudWatch Alarm:
   - Trạng thái chuyển sang màu đỏ (ALARM)

Trong Email:
   - Nhận được cảnh báo từ SNS

Trên Session Manager:
   - Kết nối bị ngắt (do máy chủ đang khởi động lại)

Trên EC2 Console:
   - Trạng thái Instance chuyển sang Stopping rồi Running

Sau khi Instance khởi động lại xong:
- Alarm sẽ tự động trở về trạng thái OK

#### Kết luận

Bạn đã xây dựng thành công hệ thống tự động khắc phục sự cố! Khi bộ nhớ vượt quá 80%, hệ thống sẽ tự động:

- Gửi cảnh báo qua email
- Kích hoạt EventBridge Rule
- Gọi Systems Manager để khởi động lại instance
- Instance tự động khởi động lại và quay trở lại trạng thái OK