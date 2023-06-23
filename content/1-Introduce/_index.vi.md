---
title : "Giới thiệu"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
Trong bài lab này, bạn sẽ thực hành tạo 1 laravel application đơn giản, có sử dụng Amazon ElastiCache Redis để lưu session, và sử dụng kết hợp Application Load Balancer (ALB) và Amazon Cognito để thực hiện chức năng xác thực (đăng kí, đăng nhập, đăng xuất).
Cụ thể, application này nằm trong 2 EC2 instance dựng phía sau ALB.
Khi user truy cập vào page public (ai cũng có thể xem được), thì ALB sẽ điều hướng tới thẳng EC2.
Nếu user truy cập vào page private (chỉ user đã đăng nhập mới có thể xem được), ALB sẽ điều hướng tới Cognito. Sau khi user tiến hành đăng nhập trên Cognito xong, ALB sẽ điều hướng user tới resource được yêu cầu trên EC2.
Với cấu trúc 2 Ec2 như vậy, để đảm bảo tính liên tục, nhất quán của session trên tất cả instance, application này sẽ sử dụng Amazon ElastiCache Redis thay vì lưu session ngay trên file driver của mỗi server.

#### Application Load Balancer (ALB)
ALB là một dịch vụ của Amazon Web Services (AWS) cung cấp các giải pháp phân phối tải và điều phối lưu lượng truy cập cho các ứng dụng chạy trên nhiều máy chủ khác nhau. 

#### Amazon Cognito
Amazon Cognito là một dịch vụ đăng nhập và quản lý xác thực cho các ứng dụng web và di động. Nó cho phép các nhà phát triển xác thực và ủy quyền người dùng thông qua các social Identity Providers (IdP) như Facebook, Google và Amazon, hoặc thông qua các tài khoản người dùng tùy chỉnh. Cognito cung cấp tính năng quản lý người dùng, phân quyền và theo dõi hoạt động người dùng, giúp giảm thiểu công sức phát triển và cải thiện bảo mật cho ứng dụng.

#### Amazon ElastiCache Redis
Amazon ElastiCache là dịch vụ tương thích với Redis và Memcache được quản lý toàn phần, mang lại hiệu năng tối ưu hóa chi phí, theo thời gian thực cho các ứng dụng hiện đại. ElastiCache mở rộng đến hàng trăm triệu thao tác mỗi giây với thời gian phản hồi tính bằng micrô giây, đồng thời đem lại độ bảo mật và độ tin cậy cấp doanh nghiệp.
Amazon ElastiCache cho Redis là lựa chọn tuyệt vời để triển khai một bộ nhớ đệm trong bộ nhớ có độ khả dụng cao, phân tán và bảo mật để giảm độ trễ truy cập, tăng năng suất và giảm tải cho cơ sở dữ liệu quan hệ hoặc NoSQL và ứng dụng của bạn.

![Architecture](/images/arc-log.png) 