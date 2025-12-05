---
title : "Tạo CloudWatch Alarm"
date: "2025-09-09"
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

#### Tạo CloudWatch Alarm

Chúng ta sẽ tạo một báo động khi RAM sử dụng vượt quá 80%.

#### Các bước thực hiện

1. **Truy cập CloudWatch Console**
   - Mở AWS Management Console và chọn **CloudWatch** service.

2. **Tạo Alarm mới**
   - Chọn **All alarms** -> **Create alarm**

![console](/images/5-Workshop/5.6-cloudwatch-alarm/console.png)

3. **Chọn Metric**
   - Nhấn **Select metric**
   - Chọn **CWAgent** -> **ImageId, InstanceId, InstanceType**
   - Tìm metric **mem_used_percent** của instance **Web-Server-Test**

![select metrics](/images/5-Workshop/5.6-cloudwatch-alarm/select-metric.png)

![select metrics2](/images/5-Workshop/5.6-cloudwatch-alarm/select-metric2.png)

4. **Cấu hình Conditions**
   - **Statistic**: Average
   - **Period**: 1 minute
   - **Threshold type**: Static
   - **Threshold value**: 50 (Lớn hơn 50%)

![condition](/images/5-Workshop/5.6-cloudwatch-alarm/condition.png)

5. **Cấu hình Actions**
   - **Notification**: Chọn **Create new topic**
   - **Topic name**: Đặt là **Admin-Alerts**
   - **Email**: Nhập email của bạn
   - Nhấn **Create topic**
   - **Lưu ý quan trọng**: Không chọn "EC2 Action" tại đây (vì metric RAM là custom metric, không hỗ trợ reboot trực tiếp). Chúng ta sẽ dùng EventBridge thay thế.
   - Nhớ kiểm tra email để **Confirm Subscription**.

![action2](/images/5-Workshop/5.6-cloudwatch-alarm/action2.png)

6. **Đặt tên Alarm**
   - **Alarm name**: **High-Memory-Auto-Reboot**
   - Nhấn **Create alarm**

Bạn đã tạo thành công CloudWatch Alarm để giám sát mức sử dụng bộ nhớ của EC2 instance.