---
title : "Triển khai ứng dụng"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b>4</b> "
---
#### Chuẩn bị ứng dụng
+ Bạn hãy tự tạo 1 repo **simpleHTML** trên account github của mình, trong repo đó chỉ cần tạo 1 file index.html đơn giản như sau.
```
<html>
  <body>
    <h1>Welcome to the demo-pipeline website</h1>
    <p>This is the index page</p>
  </body>
</html>
```
  ![EB](/images/2.prerequisite/eb/001-0.png)

#### Triển khai ứng dụng
1.  Truy cập vào [giao diện quản trị của dịch vụ Amazon Elastic Beanstalk](https://console.aws.amazon.com/elasticbeanstalk/home).
  + Click **Create application**.
  ![EB](/images/2.prerequisite/eb/001.png)
    
2. Tại màn hình **Configure environment**
  + Tại mục **Environment tier**, chọn **Web server environment**.
  + Tại mục **Application name**, nhập **demo**.
  + Tại mục **Domain**, nhập domain bạn muốn rồi ấn **Check availability** để xem có thể dùng domain đó không.
  ![EB](/images/2.prerequisite/eb/002.png)

  + Tại mục **Platform**, chọn **PHP**.
  + Tại mục **Application code**, chọn **Sample application**.
  + Scroll xuống cuối trang, click **Next**.
  ![EB](/images/2.prerequisite/eb/003.png)

3. Tại màn hình **Configure service access**
  + Tại mục **Service role**, chọn **aws-elasticbeanstalk-service-role**.
  + Tại mục **EC2 instance profile**, chọn **WebAppRole**.
  + Click **Next**
  ![EB](/images/2.prerequisite/eb/004.png)

4. Tại màn hình **Set up networking, database, and tags**
  + Tại mục **VPC**, chọn **default-vpc**.
  + Tại mục **Public IP address**, tick vào checkbox **Activated**.
  + Tại mục **Instance subnets**, chọn 1 public subnet bất kì.
  + Scroll xuống cuối trang, click **Next**
  ![EB](/images/2.prerequisite/eb/005.png)

5. Tại màn hình **Configure instance traffic and scaling**
  + Tại mục **EC2 security groups**, chọn **default**.
  ![EB](/images/2.prerequisite/eb/006.png)
  + Scroll xuống dưới, đến mục **Instance types**, chọn **t2.micro**.
  ![EB](/images/2.prerequisite/eb/008.png)
  + Scroll xuống cuối trang, click **Next**.

  6/ Tại màn hình **Configure updates, monitoring, and logging**
  + Scroll xuống cuối trang, click **Next**.

  7/ Tại màn hình **Review**
  + Scroll xuống cuối trang, click **Submit**.

 
