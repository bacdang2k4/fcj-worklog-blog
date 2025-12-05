---
title : "Cấu hình CloudWatch Agent"
date: "2025-09-09"
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

#### Cấu hình CloudWatch Agent

Vì EC2 mặc định không theo dõi chỉ số RAM (Memory), chúng ta cần cấu hình Agent để thu thập chỉ số này.

#### Các bước thực hiện

1. **Truy cập EC2 Instance qua Session Manager**
   - Tại danh sách EC2, chọn **Web-Server-Test**
   - Nhấn **Connect**
   - Chọn tab **Session Manager**
   - Nhấn **Connect** để mở giao diện dòng lệnh

![connect1](/images/5-Workshop/5.5-cloudwatch-agent/connect1.png)

![connect2](/images/5-Workshop/5.5-cloudwatch-agent/connect2.png)

2. **Tạo file cấu hình cho Agent**
   - Tạo file cấu hình bằng lệnh sau (Copy toàn bộ block và paste vào terminal):

```bash
sudo tee /opt/aws/amazon-cloudwatch-agent/bin/config.json <<EOF
{
  "agent": {
    "metrics_collection_interval": 60,
    "run_as_user": "root"
  },
  "metrics": {
    "metrics_collected": {
      "mem": {
        "measurement": [
          "mem_used_percent"
        ],
        "metrics_collection_interval": 60
      }
    }
  }
}
EOF
```

![config-agent](/images/5-Workshop/5.5-cloudwatch-agent/configagent.png)

3. Khởi động Agent để nạp cấu hình
  - Chạy lệnh sau: 

```
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -s -c file:/opt/aws/amazon-cloudwatch-agent/bin/config.json
```
Nếu không báo lỗi bạn đã cấu hình thành công CloudWatch Agent để theo dõi chỉ số bộ nhớ (Memory) của EC2 instance.