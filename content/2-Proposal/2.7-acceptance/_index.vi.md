---
title: "Nghiệm Thu"
date: "2025-09-09"
weight: 7
chapter: false
pre: " <b> 2.7 </b> "
---

# 7. Nghiệm Thu Dự Án

## 7.1 Quy Trình Nghiệm Thu

Để kết thúc dự án, quy trình nghiệm thu sẽ được thực hiện theo các bước sau:

1. **Nộp bàn giao:** Nhóm SPICA nộp **mã nguồn**, **script triển khai (Terraform)** và **báo cáo cuối cùng** cho Giảng viên/Khách hàng.
2. **Thời gian đánh giá:** Khách hàng có **5 ngày làm việc** để kiểm tra, chạy thử và xác nhận hệ thống.
3. **Ký duyệt:** Nếu tất cả các tiêu chí bên dưới đều được đáp ứng, Khách hàng sẽ ký vào **Biên bản Nghiệm Thu Dự Án**.

---

## 7.2 Tiêu Chí Nghiệm Thu

Dự án được xem là hoàn thành khi đáp ứng đầy đủ **3 nhóm tiêu chí** sau:

1. **Thiết bị Edge hoạt động đầy đủ:**
    * ESP32 chỉ mở khóa khi quét đúng **dấu vân tay đã đăng ký**.
    * Thiết bị gửi dữ liệu nồng độ cồn và dữ liệu sinh hiệu lên AWS **ngay sau khi đo**.

2. **Cổng thông tin Web hoạt động:**
    * Biên bản vi phạm xuất hiện trên website công khai trong vòng **5 giây** sau khi ghi nhận.
    * Người dùng có thể tìm kiếm vi phạm bằng **số CCCD hợp lệ**.

3. **Mã nguồn có thể triển khai lại:**
    * Toàn bộ backend có thể được khởi tạo lại tự động bằng **Terraform**, **không phát sinh lỗi**.

---

## 7.3 Từ Chối & Sửa Lỗi

* Nếu phát hiện lỗi (ví dụ: thiết bị không kết nối được, website bị crash), Khách hàng phải thông báo cho nhóm SPICA trong thời gian đánh giá.
* Nhóm có **3 ngày làm việc** để sửa lỗi và gửi lại bản cập nhật để đánh giá lại.

