---
title: "Solution Architecture"
date: "2025-09-09"
weight: 2
chapter: false
pre: " <b> 2.2 </b> "
---

# 2. Kiến Trúc Giải Pháp

## 2.1 Sơ Đồ Kiến Trúc Tổng Quan
Giải pháp sử dụng **Kiến trúc Cloud-Native Serverless** nhằm đảm bảo khả năng mở rộng cao, ít bảo trì và tiết kiệm chi phí. Hệ thống kết nối các thiết bị IoT ở Edge với backend AWS trung tâm, đi kèm nhiều lớp bảo mật toàn diện.

![Sơ đồ kiến trúc serverless AWS](/images/2-Proposal/AWS_V13.drawio.png)

**Các lớp kiến trúc chính:**
1. **Edge Layer:** ESP32 giao tiếp với các cảm biến sinh trắc học và môi trường.
2. **Ingestion & Compute Layer:** AWS IoT Core dùng cho giao tiếp an toàn và AWS Lambda xử lý logic serverless.
3. **Storage Layer:** Amazon DynamoDB lưu trữ dữ liệu rápido (NoSQL) như danh sách cảnh sát và các bản ghi vi phạm.
4. **Security & Delivery Layer:** AWS WAF bảo vệ Amplify, và API Gateway cho truy cập backend an toàn.
5. **DevOps Layer:** Tự động hóa CI/CD bằng **AWS CodePipeline** (Backend) và **AWS Amplify** (Frontend với CloudFront CDN tích hợp sẵn).

---

## 2.2 Công Nghệ Sử Dụng

Hệ thống sử dụng các dịch vụ AWS và linh kiện phần cứng như sau:

| Danh mục | Dịch vụ / Thành phần | Mục đích |
| :--- | :--- | :--- |
| **IoT & Ingestion** | **AWS IoT Core** | MQTT Broker bảo mật (TLS 1.2) cho giao tiếp thiết bị. |
| **Compute** | **AWS Lambda (Python)** | Các hàm serverless: `Authorize`, `ProcessViolation`, `GetDashboard`, `SearchByCCCD`. |
| **Database** | **Amazon DynamoDB** | Lưu bảng `DeviceOfficerMap_Pool` và `ViolationsDB` (có GSI). |
| **API Layer** | **Amazon API Gateway** | Cung cấp REST API bảo mật cho frontend. |
| **Security** | **AWS WAF** | Bảo vệ Amplify hosting khỏi các tấn công web. |
| **Frontend** | **AWS Amplify** | Hosting (với CloudFront CDN tích hợp sẵn), CI/CD cho ứng dụng React/Vue SPA. |
| **Backend DevOps** | **Terraform + GitHub Actions** | Triển khai Infrastructure as Code và tự động hóa CI/CD. |
| **Monitoring** | **Amazon CloudWatch** | Log, metric và cảnh báo lỗi hệ thống. |

### Linh kiện phần cứng tại Edge
* **Vi điều khiển:** ESP32 (Wi-Fi/Bluetooth).
* **Cảm biến:**
  * **MQ-3:** Đo nồng độ cồn.
  * **MAX30102:** Đo nhịp tim & SpO2 (an toàn sức khỏe).
  * **AS608:** Cảm biến vân tay (xác thực sinh trắc học).
* **Giao diện:** Keypad ma trận 4x4 và màn hình LCD 1602.

---

## 2.3 Quy Trình Xử Lý Chính

### A. Quy trình xác thực (Hybrid)
1. **Quét:** Cảnh sát đặt ngón tay vào cảm biến AS608.
2. **Gửi yêu cầu:** ESP32 gửi `SlotID` đã mã hóa đến AWS IoT Core qua topic `auth/request`.
3. **Xác minh:** IoT Core kích hoạt Lambda `AuthorizeFunction`.
4. **Truy vấn:** Lambda kiểm tra bảng `DeviceOfficerMap_Pool` trong DynamoDB.
5. **Phản hồi:** Hệ thống trả về lệnh `unlock` hoặc `deny`. MQ-3 chỉ hoạt động khi xác thực thành công.

### B. Quy trình ghi nhận vi phạm
1. **Đo:** Sau khi mở khóa, thiết bị liên tục đọc dữ liệu MQ-3.
2. **Nhận diện:** Nếu Nồng độ cồn > Ngưỡng, thiết bị khóa và yêu cầu nhập CCCD.
3. **Nhập liệu:** Cảnh sát nhập CCCD qua keypad.
4. **Tải lên:** Thiết bị tạo JSON gồm `OfficerID`, `AlcoholLevel`, `Timestamp`, `CCCD`, gửi lên topic `violations/new`.
5. **Xử lý:** IoT Core kích hoạt `ProcessViolationFunction` để xác thực và ghi vào `ViolationsDB`.

### C. Quy trình tra cứu công khai
1. **Tra cứu:** Người dân nhập CCCD của họ trên Web Portal.
2. **Gọi API:** Frontend gọi `GET /violations?cccd=...` qua API Gateway.
3. **Truy vấn:** Lambda `SearchByCCCDFunction` tìm dữ liệu qua GSI.
4. **Hiển thị:** Kết quả trả về và hiển thị trong < 1 giây.

---

## 2.4 Các yếu tố bảo mật

* **Bảo mật mạng:** Tất cả API được bảo vệ bởi **AWS WAF** chống SQL Injection, XSS.
* **Mã hóa dữ liệu:**
  * **In-Transit:** MQTT dùng TLS 1.2, API dùng HTTPS.
  * **At-Rest:** DynamoDB được mã hóa bằng AWS KMS.
* **Kiểm soát truy cập:**
  * **IAM Roles:** Áp dụng nguyên tắc “Least Privilege”.
  * **Device Identity:** Mỗi ESP32 có chứng chỉ X.509 riêng.
* **Quyền riêng tư:** Dữ liệu PII (CCCD) được bảo vệ nghiêm ngặt, chỉ cho phép đọc theo policy.

