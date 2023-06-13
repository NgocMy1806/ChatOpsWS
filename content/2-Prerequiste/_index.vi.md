---
title : "Các bước chuẩn bị"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---

Trong bước này, chúng ta sẽ chuẩn bị 1 số dịch vụ để có thể triển khai 1 website đơn giản có chức năng xác thực (đăng kí, đăng nhập, đăng xuất) bằng Application Load Balancer (ALB) và Amazon Cognito.

{{% notice info %}}
Để sau khi user đăng nhập thành công, user được redirect về đúng page đã yêu cầu, chúng ta cần setting 1 callback URL https trên Cognito, vì vậy, ngoài các resource cơ bản trong VPC, bạn sẽ cần chuẩn bị thêm 1 public domain name và request SSL certificate cho domain đó.
{{% /notice %}}

### Nội dung
  1. [Tạo domain](2.1-domain/)
  2. [Đăng kí SSL certificate](2.2-ssl/)
  3. [Tạo VPC](2.3-vpc/)
  4. [Tạo Security group](2.4-sg/)
  5. [Tạo EC2](2.5-ec2/)
  6. [Tạo website đơn giản trên EC2](2.6-website/)

  
