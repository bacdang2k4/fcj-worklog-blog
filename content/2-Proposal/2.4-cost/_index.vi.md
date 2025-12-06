---
title: "Cost Breakdown"
date: "2025-09-09"
weight: 4
chapter: false
pre: " <b> 2.4 </b> "
---

# 4. Phân Tích Chi Phí Dự Kiến

## 4.1 Chi Phí Vận Hành AWS (Hàng Tháng)

Ước tính chi phí sau đây dựa trên **giai đoạn Pilot**, với giả định khoảng **10.000 bản ghi vi phạm/tháng** (tương đương ~330 lượt kiểm tra/ngày) tại khu vực `ap-southeast-1` (Singapore) hoặc `us-east-1` (N. Virginia).

| Dịch vụ | Chi phí ước tính (USD) | Ghi chú |
| :--- | :--- | :--- |
| **AWS WAF** | **$6.00** | 1 Web ACL + 1 Rule Group (bắt buộc để bảo vệ API). |
| **Amazon CloudWatch** | **$2.80** | ~5GB log + 3 alarm metrics. |
| **AWS Amplify** | **$2.72** | Hosting (với CloudFront CDN tích hợp sẵn), 100 phút build, 20GB data transfer. |
| **AWS IoT Core** | **$1.00** | Chi phí kết nối & MQTT cho ~10.000 messages. |
| **AWS Lambda** | **$0.22** | ~25.000 lượt gọi (đã bao gồm Free Tier). |
| **Amazon API Gateway** | **$0.07** | ~20.000 REST API calls. |
| **Amazon DynamoDB** | **$0.02** | On-demand RCUs/WCUs (hiệu quả cao). |
| **GitHub Actions** | **$0.00** | Miễn phí cho repository công khai. |
| **TỔNG** | **~$12.83** | **Mỗi tháng** |

> **Lưu ý:** Chi phí có thể thay đổi tuỳ theo lượng data transfer và khu vực triển khai. Với Free Tier, chi phí thực tế có thể giảm xuống **< $10/tháng** trong 12 tháng đầu. Amplify hosting đã bao gồm CloudFront CDN tích hợp sẵn không tính phí thêm.

---

## 4.2 Chi Phí Phần Cứng (Một Lần)

Đây là chi phí linh kiện để chế tạo **một bộ Edge Device Prototype**.

| Thành phần | Model | Giá ước tính (USD) | Công dụng |
| :--- | :--- | :--- | :--- |
| **Vi điều khiển** | ESP32 WROOM-32 | $5.00 | Bộ xử lý chính, hỗ trợ Wi-Fi/BLE. |
| **Cảm biến nồng độ cồn** | MQ-3 Module | $3.00 | Đo nồng độ cồn trong hơi thở. |
| **Cảm biến vân tay** | AS608 Optical | $12.00 | Quét và xác thực vân tay. |
| **Cảm biến sức khỏe** | MAX30102 | $3.00 | Đo nhịp tim & SpO2. |
| **Giao diện hiển thị** | LCD 1602 + Keypad | $2.00 | Giao tiếp với người dùng. |
| **Nguồn & phụ kiện** | Pin, dây, vỏ in 3D | $3.00 | Vật tư phụ trợ. |
| **TỔNG** |  | **~$25.00** | **Mỗi thiết bị** |

---

## 4.3 Chiến Lược Tối Ưu Chi Phí

Để đảm bảo chi phí nằm trong ngân sách khi mở rộng quy mô, đội SPICA sẽ áp dụng:

1. **DynamoDB On-Demand**  
   Tránh phí khi không hoạt động; chỉ trả tiền cho đúng số lần đọc/ghi.

2. **S3 Lifecycle Policies**  
   Tự động chuyển log cũ, artifact build sang Glacier Deep Archive.

3. **Tối ưu Lambda (Power Tuning)**  
   Điều chỉnh đúng mức RAM để đạt hiệu suất tối ưu với chi phí thấp nhất.

4. **Budgets & Alarms**  
   Đặt cảnh báo AWS Budget ở mức **$15.00** – gửi email ngay khi vượt ngưỡng.

