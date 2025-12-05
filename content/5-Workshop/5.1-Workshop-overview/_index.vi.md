---
title : "Giới thiệu"
date: "2025-09-09"
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Giới thiệu về Automated Remediation

+ Automated Remediation (Khắc phục sự cố tự động) là việc sử dụng phần mềm và các quy tắc logic để phát hiện và sửa chữa các vấn đề hạ tầng mà không cần sự can thiệp của con người. Chúng là thành phần quan trọng để xây dựng hệ thống có khả năng "tự chữa lành" (self-healing), giúp giảm thiểu thời gian gián đoạn dịch vụ (downtime).
+ Tài nguyên điện toán đang chạy có thể gặp các sự cố bất thường (như tràn bộ nhớ, treo ứng dụng). Thông qua sự kết hợp giữa Amazon CloudWatch (giám sát) và AWS Systems Manager (thực thi), hệ thống có thể tự động phản ứng lại các sự cố này ngay lập tức thay vì chờ đợi kỹ sư vận hành xử lý thủ công.

#### Tổng quan về workshop
Trong workshop này, bạn sẽ triển khai một quy trình giám sát và xử lý sự cố hoàn toàn tự động.
+ **Web-Server-Test** là tài nguyên EC2 Instance đóng vai trò máy chủ ứng dụng để kiểm tra. Một **CloudWatch Agent** đã được cài đặt và cấu hình bên trong instance này để thu thập chỉ số bộ nhớ (RAM) – một chỉ số không được theo dõi mặc định bởi AWS. Bạn sẽ sử dụng công cụ stress để giả lập một cuộc tấn công làm tràn bộ nhớ, khiến máy chủ mất khả năng phản hồi.
+ **EventBridge & Systems Manager** mô phỏng đội ngũ vận hành tự động. Một quy tắc (Rule) được thiết lập để lắng nghe cảnh báo từ CloudWatch. Khi bộ nhớ vượt quá ngưỡng an toàn, hệ thống sẽ tự động kích hoạt lệnh khởi động lại (Reboot) instance thông qua Systems Manager Automation. Cơ chế này mô phỏng việc khôi phục dịch vụ nhanh chóng trong môi trường thực tế. Trong workshop này, chúng ta thực hiện hành động Reboot để thấy kết quả ngay lập tức, nhưng đối với production workloads, bạn có thể cấu hình các quy trình phức tạp hơn như dump RAM để phân tích lỗi trước khi khởi động lại hoặc thay thế instance bằng Auto Scaling.

![overview](/images/5-Workshop/5.1-Workshop-overview/ws.png)
