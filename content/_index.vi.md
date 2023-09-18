---
title : "ALB-Cognito-Redis"
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
 2. [Các bước chuẩn bị](2-Prerequiste/)
 3. [Cấu hình Slack app](3-ConfigSlackApp/)
 4. [Tạo SNS topic](4-CreateSNSTopic/)
 5. [Tạo Lambda function 1](5-Lambda1/)
 6. [Thêm stage Approval](6-ApprovalStage/)
 7. [Kiểm tra gửi noti](7-TestSendRequest/)
 8. [Tạo Lambda function 2](8-Lambda2/)
 9. [Tạo API Gateway](9-APIGateway)
 10. [Enable SlackInteractivity](10-SlackInteractivity)
 11. [Kiểm tra kết quả](11-Test/)
 12. [Dọn dẹp tài nguyên](12-cleanup/)
