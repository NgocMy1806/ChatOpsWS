---
title : "Tạo target group"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 3.1. </b> "
---

1. Truy cập vào [giao diện quản trị của dịch vụ EC2](https://console.aws.amazon.com/ec2/v2/home).
  + Click chọn **Target Groups**.
  + Click chọn **Create target groups**.
![TargetGroup](/images/3.alb/001-targetgr.png)

2. Tại màn hình tạo target group
  + Click chọn **target type** là **Instances**.
  + Nhập **Target group name** là **demo-cognito**.
  + Nhập **VPC** là **Demo-vpc**.
  + Kéo xuống cuối trang, chọn **Next**.
![TargetGroup](/images/3.alb/002-targetgr.png)

2. Tại màn hình register target 
  + Tick chọn instance vừa tạo
  + Click **Include as pending below**( nếu không chọn thì lúc truy cập bằng DNS Load Balancer sẽ gặp lỗi HTTP 503: Service unavailable).
  + Chọn **Create target group**.
![TargetGroup](/images/3.alb/003-targetgr.png)

3. Hoàn thành tạo Target group
![TargetGroup](/images/3.alb/004-targetgr.png)
