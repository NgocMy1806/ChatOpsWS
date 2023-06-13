---
title : "Session Management"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
---
# Triển khai 1 website đơn giản có chức năng xác thực bằng ALB và Amazon Cognito

### Tổng quan

 Trong bài lab này, bạn sẽ thực hành tạo 1 website đơn giản có chức năng xác thực (đăng kí, đăng nhập, đăng xuất) bằng Application Load Balancer và Amazon Cognito.
 Ngoài ra, trong quá trình làm lab, bạn cũng sẽ được giới thiệu cách để chuyển nameserver từ domain provider về Route 53, cũng như cách sửa dụng AWS Certificate Manager để request SSL certificate cho domain của bạn.
 Rất mong bài lab này sẽ giúp ích cho bạn trong "hành trình lên mây"!

![ConnectPrivate](/images/arc-log.png) 

### Nội dung

 1. [Giới thiệu](1-introduce/)
 2. [Các bước chuẩn bị](2-Prerequiste/)
 3. [Tạo ALB](3-CreateALB/)
 4. [Cấu hình Cognito](4-Cognito/)
 5. [Kiểm tra kết quả](5-Test/)
 6. [Dọn dẹp tài nguyên](6-cleanup/)
