---
title : "Giới thiệu"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
Trong bài lab này, bạn sẽ thực hành tạo 1 website đơn giản có chức năng xác thực (đăng kí, đăng nhập, đăng xuất) bằng Application Load Balancer (ALB) và Amazon Cognito.
Cụ thể, website này ở trong 1 EC2 instanace nằm phía sau ALB.
Khi user truy cập vào page public (ai cũng có thể xem được), thì ALB sẽ điều hướng tới thẳng EC2.
Nếu user truy cập vào page private (chỉ user đã đăng nhập mới có thể xem được), ALB sẽ điều hướng tới Cognito. Sau khi user tiến hành đăng nhập trên Cognito xong, ALB sẽ điều hướng user tới resource được yêu cầu trên EC2.

#### Application Load Balancer (ALB)
ALB là một dịch vụ của Amazon Web Services (AWS) cung cấp các giải pháp phân phối tải và điều phối lưu lượng truy cập cho các ứng dụng chạy trên nhiều máy chủ khác nhau. 

#### Amazon Cognito
Amazon Cognito là một dịch vụ đăng nhập và quản lý xác thực cho các ứng dụng web và di động. Nó cho phép các nhà phát triển xác thực và ủy quyền người dùng thông qua các social Identity Providers (IdP) như Facebook, Google và Amazon, hoặc thông qua các tài khoản người dùng tùy chỉnh. Cognito cung cấp tính năng quản lý người dùng, phân quyền và theo dõi hoạt động người dùng, giúp giảm thiểu công sức phát triển và cải thiện bảo mật cho ứng dụng.

![ConnectPrivate](/images/arc-log.png) 