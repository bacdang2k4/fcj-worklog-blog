---
title: "Worklog Tuần 11"
date: "2025-09-09"
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11:

* Xây dựng hạ tầng AWS bằng Terraform.
* Thiết lập GitHub Actions để tự động deploy.
* Hoàn thiện pipeline CI/CD cho backend.
* Đảm bảo bảo mật và tổ chức hạ tầng theo kiến trúc dự án.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Phân tích kiến trúc hệ thống và xác định các tài nguyên AWS cần triển khai                                                                                             | 17/11/2025   | 17/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Viết Terraform cho các dịch vụ chính: S3, DynamoDB, IAM                                            | 18/11/2025   | 18/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Triển khai IoT Core, Lambda và API Gateway bằng Terraform | 19/11/2025   | 19/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Cấu hình Terraform backend                  | 20/11/2025   | 20/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Thiết lập GitHub Actions cho Terraform plan / apply                                                                                        | 21/11/2025   | 21/11/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 11:

* Hoàn thành cấu trúc hạ tầng AWS bằng Terraform.
* Triển khai thành công các dịch vụ quan trọng:
  - AWS IoT Core
  - Lambda
  - API Gateway
  - DynamoDB
  - IAM
* Cấu hình Terraform remote state bằng S3 và khóa bằng DynamoDB.
* Xây dựng pipeline GitHub Actions tự động:
  - Chạy `terraform init`
  - `terraform plan`
  - `terraform apply`
* Pipeline hoạt động ổn định, có thể deploy lại nhiều lần không lỗi.
* Hạ tầng bám sát sơ đồ kiến trúc dự án.