---
title : "ALB-Cognito-Redis"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
---
# Triển khai 1 application đơn giản sử dụng Amazon ElastiCache Redis để lưu session, sử dụng kết hợp ALB và Amazon Cognito để xác thực user

### Tổng quan

 Trong bài lab này, bạn sẽ thực hành tạo 1 laravel application đơn giản, có sử dụng Amazon ElastiCache Redis để lưu session, và sử dụng kết hợp Application Load Balancer (ALB) và Amazon Cognito để thực hiện chức năng xác thực (đăng kí, đăng nhập, đăng xuất).

 Ngoài ra, trong quá trình làm lab, bạn cũng sẽ được giới thiệu cách để chuyển nameserver từ domain provider về Route 53, cách sử dụng AWS Certificate Manager để request SSL certificate cho domain, cách sử dụng Elastic Beanstalk để triển khai ứng dụng một cách nhanh chóng.
 
 Rất mong bài lab này sẽ giúp ích cho bạn trong "hành trình lên mây"!


![ConnectPrivate](/images/arc-log.png) 

### Nội dung

 1. [Giới thiệu](1-introduce/)
 2. [Các bước chuẩn bị](2-Prerequiste/)
 3. [Cấu hình Cognito](3-Cognito/)
 4. [Triển khai ứng dụng](4-Deploy/)
 5. [Cấu hình ALB](5-ConfigALB/)
 6. [Cấu hình DNS](6-DNS/)
 7. [Cấu hình Redis cluster](7-RedisCluster/)
 8. [Hiện trạng trước khi dùng Redis](8-BeforeApplyRedis/)
 9. [Kiểm tra kết quả](9-Test/)
 10. [Dọn dẹp tài nguyên](10-cleanup/)
