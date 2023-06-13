---
title : "Tạo VPC "
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---


#### Tạo VPC, subnets, route tables, internet gateway
1. Truy cập [giao diện quản trị dịch vụ VPC](https://console.aws.amazon.com/vpc/home)
  + Click **Your VPCs**.
  + Click **Create VPC**.

![VPC](/images/2.prerequisite/001-createvpc.png)

2. Tại trang **Create VPC**.
  + Tại mục **Name tag** điền **Demo VPC**.
  + Tại mục **IPv4 CIDR** điền : **10.10.0.0/16**.
  + Tại mục **Number of Availability Zones (AZs)** chọn : **2**.
  + Tại mục **Number of public subnets** chọn : **2**.
  + Tại mục **Number of private subnets** chọn : **0**.
  + Tại mục **VPC endpoints** chọn : **None**.
  + Click **Create VPC** ở cuối trang.

![VPC](/images/2.prerequisite/002-createvpc.png)

3. Xem thông tin chi tiết VPC vừa tạo
![VPC](/images/2.prerequisite/003-detailvpc.png)

4. Thực hiện cấp phát IP public cho public subnet 1
  + Mở menu **Subnet**.
  + Chọn **PublicSubnet1**.
  + Chọn **Edit subnet settings**.
  ![VPC](/images/2.prerequisite/004-enablepublicIPforsubnet.png)

  + Tick vào ô **Enable auto-assign public IPv4 address**
    ![VPC](/images/2.prerequisite/005-enablepublicIP.png)
  + Cick button **Save**

5. Kiểm tra đã cấp phát thành công
![VPC](/images/2.prerequisite/006-enablesuccess.png)

6. Thực hiện cấp phát cho Public subnet còn lại (làm tương tự).