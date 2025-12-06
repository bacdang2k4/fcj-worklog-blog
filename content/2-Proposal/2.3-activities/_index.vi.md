---
title: "Activities & Deliverables"
date: "2025-09-09"
weight: 3
chapter: false
pre: " <b> 2.3 </b> "
---

# 3. Hoạt Động & Sản Phẩm Bàn Giao

## 3.1 Ma Trận Hoạt Động và Sản Phẩm Bàn Giao

Dự án được triển khai trong **12 tuần**, theo phương pháp Agile với chu kỳ sprint 2 tuần.

| Giai đoạn dự án | Thời gian | Hoạt động chính | Sản phẩm / Mốc hoàn thành | Ước tính công sức |
| :--- | :--- | :--- | :--- | :--- |
| **I. Thiết kế & Nền tảng** | Tuần 1–2 | • Hoàn thiện Kiến trúc & DB Schema<br>• Thiết lập AWS Account & IAM Roles<br>• Khởi tạo Terraform State (S3) | • Tài liệu Kiến trúc (LLD)<br>• Terraform Backend<br>• Thiết kế CSDL | 10 man-days |
| **II. Phát triển Firmware** | Tuần 3–4 | • Kết nối ESP32 với AS608, MQ-3, MAX30102<br>• Triển khai logic xác thực MQTT<br>• Hiệu chỉnh cảm biến | • ESP32 đã nạp firmware<br>• Gửi được “Hello World” lên IoT Core<br>• Log dữ liệu từ cảm biến | 15 man-days |
| **III. Backend Services** | Tuần 5–7 | • Phát triển Lambda Functions (Python)<br>• Cấu hình API Gateway & Rules Engine<br>• Triển khai Backend tự động | • Serverless Stack đã triển khai<br>• REST API hoạt động<br>• Backend tự động hóa | 20 man-days |
| **IV. Phát triển Frontend** | Tuần 8–9 | • Xây dựng Web Portal (React/Vue)<br>• Tích hợp API & Cognito (nếu dùng)<br>• Thiết lập AWS Amplify Hosting | • URL Website công khai<br>• Giao diện Dashboard Admin<br>• Chức năng tra cứu công dân | 15 man-days |
| **V. Bảo mật & Kiểm thử** | Tuần 10–11 | • Cấu hình AWS WAF Rules<br>• Kiểm thử End-to-End<br>• Quét bảo mật (tfsec) | • Báo cáo kiểm thử bảo mật<br>• UAT Sign-off<br>• Cấu hình WAF ACL | 10 man-days |
| **VI. Chuyển giao & Đóng dự án** | Tuần 12 | • Demo cuối với Stakeholders<br>• Tài liệu & chuyển giao kiến thức<br>• Dọn dẹp tài nguyên sandbox | • Báo cáo dự án cuối cùng<br>• Repository mã nguồn<br>• Tài liệu hướng dẫn sử dụng | 5 man-days |

---

## 3.2 Phạm Vi Loại Trừ (Out of Scope)

Các hạng mục sau được **loại trừ** khỏi PoC nhằm đảm bảo tiến độ và phạm vi tập trung trong 12 tuần:

* **Ứng dụng di động:** Không phát triển app iOS/Android; Web Portal responsive đủ cho thiết bị di động.
* **Thiết kế phần cứng công nghiệp:** Prototype dùng breadboard hoặc case in 3D, không làm vỏ tiêu chuẩn IP67.
* **Giá trị pháp lý:** Dữ liệu cảm biến nồng độ cồn chỉ phục vụ mục đích kỹ thuật, **không sử dụng cho xử phạt pháp lý**.
* **Tích hợp hệ thống cũ:** Không tích hợp với server SQL on-premise hay các database cũ của cơ quan chức năng.

---

## 3.3 Lộ Trình Lên Production

Hệ thống hiện tại là **Technical Proof of Concept (PoC)**. Để chuyển sang môi trường Production thực tế, cần triển khai các bước sau:

1. **Đảm bảo tính sẵn sàng cao (High Availability):**
   * Bật **DynamoDB Global Tables** để nhân bản đa vùng.
   * Triển khai API Gateway trên nhiều Availability Zones (AZ).

2. **Khả năng hoạt động ngoại tuyến:**
   * Cài **AWS IoT Greengrass** trên gateway cục bộ để buffer dữ liệu vi phạm khi mất kết nối mạng.

3. **Tăng cường bảo mật:**
   * Di chuyển cấu hình và secret ra **AWS Secrets Manager**.
   * Thực hiện Penetration Testing bởi bên thứ 3.

4. **Vận hành chuyên nghiệp (Operational Excellence):**
   * Tạo cảnh báo nâng cao bằng **CloudWatch Anomaly Detection**.
   * Xây dựng **Incident Response Plan** chính thức.
