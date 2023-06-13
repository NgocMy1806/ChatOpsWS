---
title : "Tạo EC2"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 2.5</b> "
---

1. Truy cập [giao diện quản trị dịch vụ EC2](https://console.aws.amazon.com/ec2/v2/home) để tạo instance
  + Click **Instances**.
  + Click **Launch instances**.
  
![EC2](/images/2.prerequisite/011-1-ec2.png)

  + Nhập tên cho instance là **demo-ec2** 
  + Chọn AMI **Amazon Linux 2 AMI**.
  ![EC2](/images/2.prerequisite/011-ec2.png)
  + Click chọn Instance type **t2.micro**.
  + Click chọn keypair hiện có hoặc tạo mới (nếu bạn định dùng EC2 instnace connect để kết nối vào ec2 thì có thể không cần key pair).
  + Tại mục **Network** chọn **Demo-vpc**.
  + Tại mục **Subnet** chọn **Public Subnet1**.
  + Tại mục **Auto-assign Public IP** chọn **Enable**
    ![EC2](/images/2.prerequisite/012-ec2.png)
  + Chọn **Select an existing security group**.
  + Chọn security group **SG Public Linux Instance**.
  + Click **Launch Instance**.
  ![EC2](/images/2.prerequisite/013-ec2.png)

Sau khi instance khởi tạo thành công, bạn sẽ chuyển sang bước tiếp theo để tạo website đơn giản trên ec2
