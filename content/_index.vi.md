---
title : "Chatops"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
---
# Triển khai Chatops với AWS service và Slack

### Tổng quan

 Trong bài lab này, mình sẽ giới thiệu với các bạn cách triển khai Chatops với AWS service và Slack.
 Đây là bài lab đơn giản để bạn hiểu được chatops là gì, cách triển khai chatops ở mức cơ bản, sau khi làm xong, bạn có thể ứng dụng vào dự án thực tế với những config phức tạp hơn (VD chỉ định user được quyền ấn button Approve trên Slack, thêm stage build code, config AWS chatbot để có thể gõ command trực tiếp trên Slack,….)
 
 Rất mong bài lab này sẽ giúp ích cho bạn trong "hành trình lên mây"!


![Architecture](/images/arc-log.png) 

### Nội dung

 1. [Giới thiệu](1-introduce/)
 2. [Các bước chuẩn bị](2-prerequiste/)
 3. [Cấu hình Slack app](3-createsnstopic/)
 4. [Tạo SNS topic](4-createsnstopic/)
 5. [Tạo Lambda function 1](5-lambda1/)
 6. [Thêm Approval stage](6-approvalstage/)
 7. [Kiểm tra gửi noti](7-testsendrequest/)
 8. [Tạo Lambda function 2](8-lambda2/)
 9. [Tạo API Gateway](9-apigateway)
 10. [Enable SlackInteractivity](10-slackinteractivity)
 11. [Kiểm tra kết quả](11-test/)
 12. [Dọn dẹp tài nguyên](12-cleanup/)
