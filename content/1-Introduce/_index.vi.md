---
title : "Giới thiệu"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
Trong bài lab này, mình sẽ giới thiệu với các bạn cách triển khai Chatops với AWS service và Slack.

ChatOps là 1 từ được tạo ra bằng cách kết hợp 2 từ Chat và Ops (operation). Đây là phương pháp thực hiện các công việc liên quan đến triển khai, vận hành hệ thống ngay trên các tool chat như Slack, Microsoft Teams, Telegram,… 

ChatOps có thể được sử dụng để tự động hóa một loạt các quy trình như:

- Khởi chạy các ứng dụng
- Truy cập dữ liệu
- Tạo và cập nhật dữ liệu
- Gửi email và thông báo
- Tạo và quản lý các nhiệm vụ
- Hỗ trợ khách hàng
- Quản lý dự án
- Theo dõi tiến độ
- …

Trong phạm vi bài lab này, mình sẽ tập trung vào thực hành gửi thông báo về trạng thái của pipeline vào channel Slack, và triển khai ứng dụng nhanh chóng chỉ bằng 1 click chuột ngay trên Slack.

Flow tổng thể như sau:
  
   Bạn thực hiện thay đổi và merge code vào branch master

→ Pipeline được khởi động

→ Đến approval stage, pipeline sẽ gửi thông báo đến AWS SNS, rồi SNS trigger Lambda function để gửi request approve đến channel Slack

→ user ấn button Approve hoặc Reject trên Slack

→ kết quả approve được gửi đến CodePipeline thông qua API gateway và Lambda function

→ Nếu OK, CodePipeline sẽ tiến hành deploy.

#### AWS CodePipeline
AWS CodePipeline là dịch vụ phân phối liên tục được quản lý hoàn toàn giúp bạn tự động hóa các quy trình phát hành để cung cấp các bản cập nhật về ứng dụng và cơ sở hạ tầng một cách nhanh chóng và ổn định.

#### API gateway
Amazon API Gateway là dịch vụ được quản lý hoàn toàn giúp các nhà phát triển dễ dàng tạo, phát hành, duy trì, giám sát và bảo vệ API ở mọi quy mô. API đóng vai trò là "cửa vào" cho các ứng dụng để truy cập dữ liệu, logic nghiệp vụ hoặc chức năng từ các dịch vụ backend của bạn. Bằng cách sử dụng API Gateway, bạn có thể tạo các API RESTful và API WebSocket để kích hoạt các ứng dụng giao tiếp hai chiều theo thời gian thực. API Gateway hỗ trợ các khối lượng công việc có trong container và serverless, cũng như các ứng dụng web.

#### Amazon SNS
Amazon Simple Notification Service (SNS) là một dịch vụ của Amazon Web Services (AWS) được sử dụng để tạo, quản lý và gửi thông báo hoặc tin nhắn tới nhiều điểm cuối khác nhau, bao gồm ứng dụng di động, máy chủ, máy tính cá nhân và các dịch vụ khác của AWS.

![Architecture](/images/arc-log.png) 