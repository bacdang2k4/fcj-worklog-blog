---
title: "Worklog Tuần 7"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

* Tìm hiểu về AWS Lambda
* Tìm hiểu AWS CLI và cách deploy java function lên Lambda bằng AWS CLI
* Tìm hiểu cách API Gateway và Lambda làm việc với nhau

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tìm hiểu tổng quan về AWS Lambda: khái niệm, kiến trúc hoạt động, ưu điểm của mô hình serverless và cách Lambda thực thi mã nguồn.                                                                                            | 20/10/2025   | 20/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   |- Nghiên cứu AWS CLI: chức năng, cách cài đặt và cấu hình truy cập tài khoản AWS bằng IAM User; tìm hiểu cú pháp các lệnh cơ bản.                                  | 21/10/2025   | 21/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Thực hành cài đặt AWS CLI trên máy cá nhân, cấu hình thông tin xác thực và thử nghiệm một số lệnh quản lý tài nguyên (S3, EC2, Lambda).| 22/10/2025   | 22/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Tìm hiểu quy trình triển khai Java Function lên AWS Lambda: chuẩn bị project Maven, đóng gói file .jar, tạo và upload function bằng AWS CLI.                  | 23/10/2025   | 23/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Thực hành triển khai Java Function lên Lambda bằng AWS CLI, gán quyền IAM phù hợp và kiểm thử hoạt động của function.                                                                     | 24/10/2025   | 24/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 7   | - Tìm hiểu cách API Gateway kết nối với AWS Lambda để xây dựng API backend; cấu hình endpoint và kiểm thử gọi API.                                                                     | 25/10/2025   | 25/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| CN   | - Tổng hợp kiến thức đã học: mối quan hệ giữa Lambda – API Gateway – AWS CLI, ghi lại quy trình triển khai và chuẩn bị báo cáo tuần. - Viết **nhật ký công việc tuần 7**                                                                    | 26/10/2025   | 26/10/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 7:

#### 1. Hiểu rõ về AWS Lambda
- Nắm được khái niệm và vai trò của **AWS Lambda** trong mô hình *serverless*.
- Hiểu cơ chế hoạt động của Lambda: quá trình kích hoạt (trigger), thực thi function và trả kết quả.
- Phân biệt sự khác nhau giữa **Lambda** và **EC2** về:
  - Quản lý hạ tầng
  - Chi phí sử dụng
  - Khả năng mở rộng và tính linh hoạt.

#### 2. Nắm được cách sử dụng AWS CLI
- Cài đặt và cấu hình **AWS CLI** thành công trên máy cá nhân bằng IAM User.
- Thực hành các lệnh cơ bản:
  - Liệt kê bucket S3.
  - Tạo và xem thông tin Lambda function.
  - Quản lý các tài nguyên cơ bản trên AWS.
- Hiểu cách AWS CLI gửi yêu cầu API và cơ chế xác thực bằng Access Key/Secret Key.

#### 3. Thực hành triển khai Java Function lên AWS Lambda bằng AWS CLI
- Xây dựng project Java sử dụng **Maven**, tạo class handler và đóng gói thành file `.jar`.
- Dùng lệnh `aws lambda create-function` để upload và triển khai function.
- Gán **IAM Role** phù hợp để Lambda có quyền thực thi.
- Kiểm tra hoạt động của function bằng lệnh:
  ```bash
  aws lambda invoke --function-name <FunctionName> output.txt

