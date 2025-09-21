---
title: "Blog 2"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# Giúp khách hàng triển khai AI agent sẵn sàng cho sản xuất ở quy mô lớn

AI agent đang mở ra một cuộc cách mạng công nghệ mới, tương tự như sự ra đời của Internet. AWS cam kết xây dựng nền tảng tốt nhất để phát triển và triển khai AI agent an toàn, đáng tin cậy và có khả năng mở rộng. Các ứng dụng thực tế đã cho thấy tiềm năng lớn trong y tế (AstraZeneca), tài chính (Yahoo Finance), và nông nghiệp (Syngenta). Để mở rộng thành công này, AWS tập trung cung cấp các công cụ và nền tảng giúp tổ chức dễ dàng chuyển AI agent từ thử nghiệm sang sản xuất, với trọng tâm là bảo mật, độ tin cậy và khả năng thích ứng theo thời gian.

---

## Nguyên tắc cốt lõi cho Agentic AI

AWS định hướng dựa trên **4 nguyên tắc chính**:

1. **Tính linh hoạt (Agility)**  
   - Xây dựng hệ thống mô-đun, dễ mở rộng và thích ứng khi mô hình, tính năng hoặc yêu cầu thay đổi.  

2. **Phát triển nền tảng cơ bản (Evolve Fundamentals)**  
   - Bảo mật & Tin cậy: cô lập session, bộ nhớ, phục hồi và mở rộng cho nhiều người dùng đồng thời.  
   - Quản lý danh tính & quyền hạn: tích hợp với hệ thống IAM và identity provider.  
   - Quan sát & giám sát: theo dõi, telemetry theo thời gian thực.  
   - Truy cập dữ liệu: kết hợp dữ liệu riêng một cách an toàn.  
   - Tích hợp liền mạch: làm việc với công cụ, cloud, API và các agent khác.  

3. **Hiệu quả với mô hình & dữ liệu (Model Choice & Data)**  
   - Cho phép lựa chọn mô hình phù hợp (chi phí, tốc độ, khả năng suy luận…).  
   - Cung cấp công cụ tùy chỉnh: fine-tuning, alignment, huấn luyện trước & sau.  
   - Nova Customization: tùy chỉnh linh hoạt (PEFT, fine-tuning đầy đủ…).  
   - Nova Act: hỗ trợ tác vụ tự động trên trình duyệt.  
   - **Amazon S3 Vectors**: lưu trữ vector embedding rẻ hơn ~90% nhưng vẫn đảm bảo hiệu năng, giúp agent có trí nhớ và ngữ cảnh phong phú hơn.  

4. **Triển khai giải pháp tạo giá trị (Deploy Transformative Solutions)**  
   - Cung cấp sẵn công cụ/agent thay vì để khách hàng xây từ đầu.  
   - Marketplace: kho ứng dụng và agent do AWS và đối tác phát triển.  
   - Ví dụ:  
     - **Kiro**: IDE cho phát triển dựa trên specification.  
     - **AWS Transform**: hỗ trợ phân tích mã nguồn và hiện đại hóa hệ thống.  
     - **Amazon Connect**: tích hợp AI agents trong dịch vụ khách hàng.  

---

## Các dịch vụ & tính năng mới

- **AgentCore**: bộ dịch vụ vận hành agents quy mô doanh nghiệp (runtime, identity, observability, memory, browser, code interpreter…).  
- **Nova Customization trên SageMaker AI**: mở rộng khả năng tùy chỉnh mô hình (pre-training, fine-tuning, alignment).  
- **Nova Act SDK**: công cụ preview cho AI agents tự động hóa trình duyệt.  
- **Amazon S3 Vectors**: hỗ trợ vector gốc trong S3, giảm chi phí lưu trữ vector ~90%.  
- **Marketplace Agents & Tools**: kho các agent và công cụ sẵn sàng triển khai từ AWS Partner.  
- **Pre-built Solutions**: như Kiro, AWS Transform giúp rút ngắn thời gian từ ý tưởng đến sản phẩm thực tế.  

---

## Hướng đi & Khuyến nghị

- **Bắt đầu ngay**: chọn một vấn đề cụ thể trong kinh doanh để thử nghiệm.  
- **Lặp nhanh**: thu thập phản hồi thực tế và cải tiến liên tục.  
- **Hỗ trợ từ AWS**: thông qua Generative AI Innovation Center và các dịch vụ tư vấn chuyên sâu.  

---

## Kết luận

AWS đang xây dựng nền tảng toàn diện để giúp tổ chức **xây dựng, tùy chỉnh, bảo mật và mở rộng AI agents**. Với các dịch vụ mới như **AgentCore, Nova, S3 Vectors**, mục tiêu là đưa AI agents từ thử nghiệm sang **sản xuất**, đảm bảo **tin cậy, thích ứng và mang lại giá trị kinh doanh thực sự**.
