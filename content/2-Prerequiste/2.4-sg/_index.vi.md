---
title : "Tạo security group"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 2.4</b> "
---

#### Tạo các security groups

Trong bước này chúng ta sẽ tiến hành tạo các security groups cho ALB, instance và ElastiCache Redis cluster. 

#### Tạo security group cho ALB 

1. Truy cập [giao diện quản trị dịch vụ VPC](https://console.aws.amazon.com/vpc)
  + Click **Security Group**.  
  + Click **Create security group**.

![SG](/images/2.prerequisite/019-createsg.png)

3. Tại màn hình **Create security group**
  + Tại mục **Security group name**, điền **SG ALB**. 
  + Tại mục **Description**, điền **SG ALB**.
  + Tại mục **VPC**, click dấu **X** để chọn lại **Demo-vpc** bạn đã tạo cho bài lab này.

![SG](/images/2.prerequisite/007-createsgalb.png)

4. Cấu hình **Inbound rule** 
  + Tạo 2 inbound rule cho phép nhận traffic từ port 80 và 443 từ internet như sau
  ![SG](/images/2.prerequisite/008-createsgalb1.png)

5. Giữ nguyên **Outbound rule**, kéo chuột xuống phía dưới.
  + Click **Create security group**.

#### Tạo security group cho Linux instance nằm trong public subnet 

1. Truy cập [giao diện quản trị dịch vụ VPC](https://console.aws.amazon.com/vpc)
  + Click **Security Group**.  
  + Click **Create security group**.

![SG](/images/2.prerequisite/019-createsg.png)

3. Tại mục **Security group name**, điền **SG Public Linux Instance**. 
  + Tại mục **Description**, điền **SG Public Linux Instance**.
  + Tại mục **VPC**, click dấu **X** để chọn lại **Demo-vpc** bạn đã tạo cho bài lab này.

![SG](/images/2.prerequisite/009-createec2sg.png)

4. Cấu hình **Inbound rule** 
  + EC2 instance không nhận traffic trực tiếp từ user, mà nhận thông qua ALB, vì vậy, chúng ta sẽ cấu hình inbound rule chỉ cho phép nhận traffic thông qua giao thức http, port 80 từ source là Security group của ALB.
  + Tiếp theo, để có thể SSH vào instance, chúng ta cần tạo thêm inbound rule cho port 22 từ **My IP**.
  ![SG](/images/2.prerequisite/010-createec2sg1.png)

5. Giữ nguyên **Outbound rule**, kéo chuột xuống phía dưới.
  + Click **Create security group**.


#### Tạo security group cho ElastiCache Redis cluster

1. Truy cập [giao diện quản trị dịch vụ VPC](https://console.aws.amazon.com/vpc)
  + Click **Security Group**.  
  + Click **Create security group**.

![SG](/images/2.prerequisite/019-createsg.png)

3. Tại mục **Security group name**, điền **SG Redis**. 
  + Tại mục **Description**, điền **SG Redis**.
  + Tại mục **VPC**, click dấu **X** để chọn lại **Demo-vpc** bạn đã tạo cho bài lab này.

![SG](/images/2.prerequisite/011-createredissg.png)

4. Cấu hình **Inbound rule** 
  + Để có thể giao tiếp với EC2, chúng ta cần mở inbound rule cho port 6379 từ source là Security group của EC2 như sau.

![SG](/images/2.prerequisite/012-createredissg.png)

5. Giữ nguyên **Outbound rule**, kéo chuột xuống phía dưới.
  + Click **Create security group**.

#### Bổ sung inbound rule cho security group của Linux instance 

  Để EC2 có thể giao tiếp với Redis cluster, chúng ta cần thực hiện các bước sau:
  + Từ màn hình **Security groups**, chọn **SG Pulic Linux Instance**.
  + Chọn tab **Inbound rules**, rồi click **Edit inbound rules**.
    ![SG](/images/2.prerequisite/011-createec2sg.png)
  + Tại màn hình **Edit inbound rules**, mở thêm inbound rule cho port 6379 từ source là Security group của Redis cluter.
    ![SG](/images/2.prerequisite/012-createec2sg.png)
    
    Như vậy chúng ta đã tạo xong các security group cần thiết cho các EC2 instance, ALB và ElastiCache Redis cluster.