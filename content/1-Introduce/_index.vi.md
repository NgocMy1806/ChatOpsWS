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

Với cấu trúc 2 EC2 như vậy, để đảm bảo tính liên tục, nhất quán của session trên tất cả instance, application này sẽ sử dụng Amazon ElastiCache Redis thay vì lưu session ngay trên file driver của mỗi server.

Ngoài ra, bài lab này cũng sẽ hướng dẫn bạn cách triển khai hệ thống một cách nhanh chóng, linh hoạt, đảm bảo high availability thông qua dịch vụ Elastic Beanstalk.

#### Application Load Balancer (ALB)
ALB là một dịch vụ của Amazon Web Services (AWS) cung cấp các giải pháp phân phối tải và điều phối lưu lượng truy cập cho các ứng dụng chạy trên nhiều máy chủ khác nhau. 

#### Amazon Cognito
Amazon Cognito là một dịch vụ đăng nhập và quản lý xác thực cho các ứng dụng web và di động. Nó cho phép các nhà phát triển xác thực và ủy quyền người dùng thông qua các social Identity Providers (IdP) như Facebook, Google và Amazon, hoặc thông qua các tài khoản người dùng tùy chỉnh. Cognito cung cấp tính năng quản lý người dùng, phân quyền và theo dõi hoạt động người dùng, giúp giảm thiểu công sức phát triển và cải thiện bảo mật cho ứng dụng.

#### Amazon ElastiCache Redis
Amazon ElastiCache là dịch vụ tương thích với Redis và Memcache được quản lý toàn phần, mang lại hiệu năng tối ưu hóa chi phí, theo thời gian thực cho các ứng dụng hiện đại. ElastiCache mở rộng đến hàng trăm triệu thao tác mỗi giây với thời gian phản hồi tính bằng micrô giây, đồng thời đem lại độ bảo mật và độ tin cậy cấp doanh nghiệp.
Amazon ElastiCache cho Redis là lựa chọn tuyệt vời để triển khai một bộ nhớ đệm trong bộ nhớ có độ khả dụng cao, phân tán và bảo mật để giảm độ trễ truy cập, tăng năng suất và giảm tải cho cơ sở dữ liệu quan hệ hoặc NoSQL và ứng dụng của bạn.

#### AWS Elastic Beanstalk 
Elastic Beanstalk cung cấp một nền tảng đơn giản để triển khai các ứng dụng web mà không yêu cầu kiến thức chuyên sâu về hạ tầng. Bằng cách sử dụng Elastic Beanstalk, bạn có thể tập trung vào việc phát triển ứng dụng của mình mà không phải quan tâm đến việc cấu hình và quản lý các tài nguyên cơ sở hạ tầng như máy chủ, mạng và cơ sở dữ liệu.

  {{% notice info %}}
  Đây là bài lab mở rộng từ bài lab "Triển khai 1 website đơn giản có chức năng xác thực bằng ALB và Amazon Cognito". 

  Danh sách chức năng bổ sung: Xử lí logout ở phía backend (xóa cookie của ALB); Xử lí decode header của ALB để hiển thị thông tin user lấy từ Cognito; Lưu session trên Redis Cluster.
  Bạn có thể mở source code để xem chi tiết cách làm.
  {{% /notice %}}

![Architecture](/images/arc-log.png) 