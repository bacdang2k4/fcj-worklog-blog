---
title: "Bối cảnh & Động lực"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 2.1 </b> "
---

# 1. Bối cảnh & Động lực

## 1.1 Tóm tắt Điều hành (Executive Summary)

### Bối cảnh Khách hàng
Khách hàng là **Đại học FPT TP.HCM (Hội đồng Học thuật)** dưới sự hướng dẫn của **Nguyễn Gia Hưng** và tiềm năng cho các Cơ quan Xử lý Vi phạm Giao thông. Họ mong muốn một mô hình minh họa công nghệ về cách **IoT** và **Điện toán Đám mây** có thể giải quyết các vấn đề thực tế trong giám sát giao thông. Quy trình kiểm tra nồng độ cồn thủ công hiện tại gặp nhiều hạn chế: không xác thực được người vận hành, dữ liệu phân tán và thiếu minh bạch đối với người dân.

### Mục tiêu Kinh doanh & Kỹ thuật
**Team SPICA** đề xuất giải pháp **“IoT-Based Alcohol Violation Detection System”** nhằm hiện đại hóa quy trình này.  
Các mục tiêu chính gồm:

* **Trách nhiệm giải trình (Accountability):** Loại bỏ việc sử dụng thiết bị trái phép bằng cách áp dụng **Xác thực Sinh trắc học (Vân tay)** cho mỗi phiên sử dụng.
* **Minh bạch:** Cho phép người dân tự tra cứu lịch sử vi phạm của chính họ qua **Cổng Web Công khai**.
* **Tối ưu vận hành:** Thay thế giấy tờ thủ công bằng cơ sở dữ liệu đám mây **Serverless**, tự động và không thể chỉnh sửa.

### Các Trường hợp Sử dụng Chính (Key Use Cases)
1. **Kích hoạt thiết bị an toàn:** Cảnh sát/nhân viên hiện trường phải quét vân tay trên **Thiết bị Edge ESP32**. Hệ thống xác thực đối chiếu với DynamoDB thông qua **AWS IoT Core** trước khi mở khóa cảm biến.
2. **Thu thập dữ liệu đa cảm biến:** Thiết bị đồng thời đo **Nồng độ cồn (MQ-3)** và **Chỉ số sức khỏe (Nhịp tim/SpO₂ qua MAX30102)** để đảm bảo an toàn cho người được kiểm tra.
3. **Ghi nhận vi phạm theo thời gian thực:** Dữ liệu vi phạm được mã hóa và đồng bộ ngay lập tức lên AWS, và có thể được xem qua Dashboard (cho admin) hoặc Cổng tra cứu (cho người dân).

---

## 1.2 Tiêu chí Thành công của Dự án

Để được xem là thành công, hệ thống phải đáp ứng các chỉ số định lượng sau:

| Chỉ số | Mục tiêu | Ghi chú |
| :--- | :--- | :--- |
| **Độ trễ xác thực** | **< 2 giây** | Thời gian từ lúc quét vân tay → xác thực Cloud → mở khóa thiết bị. |
| **Độ toàn vẹn dữ liệu** | **99.9%** | Không mất dữ liệu vi phạm trong các bài kiểm tra mạng. |
| **Tuân thủ bảo mật** | **100%** | Mọi Terraform phải vượt qua kiểm tra **tfsec** trong CI/CD. |
| **Tự động triển khai** | **Hoàn toàn tự động** | Backend deploy qua **Terraform + GitHub Actions**; Frontend deploy qua **AWS Amplify**. |
| **Chi phí tối ưu** | **< 15 USD/tháng** | Chi phí vận hành AWS cho giai đoạn thử nghiệm. |

---

## 1.3 Giả định & Ràng buộc

### Phần cứng & Kết nối
* **Thiết bị:** Nhóm đã chuẩn bị ESP32 WROOM, AS608 (vân tay), MQ-3 (nồng độ cồn) và MAX30102 (nhịp tim/SpO₂).
* **Kết nối:** Thiết bị Edge được giả định luôn có Wi-Fi ổn định hoặc hotspot 4G trong quá trình vận hành.

### Môi trường Kỹ thuật
* **Truy cập Cloud:** Team SPICA có quyền Administrator trên tài khoản AWS dành riêng cho dự án.
* **Công nghệ phát triển:**
    * **Firmware:** C++ / PlatformIO  
    * **Backend:** Python (Lambda) & Terraform (IaC)  
    * **Frontend:** React/Vue.js trên S3/Amplify  

### Giới hạn Phạm vi
* **Tính pháp lý:** Đây là dự án Proof of Concept (PoC). Các số đo cảm biến chỉ mang tính minh họa và không có giá trị pháp lý mà không có hiệu chuẩn công nghiệp.
* **Thiết kế vỏ thiết bị:** Prototype sử dụng vỏ mica hoặc 3D-printed tạm thời, không phải tiêu chuẩn công nghiệp IP67.

