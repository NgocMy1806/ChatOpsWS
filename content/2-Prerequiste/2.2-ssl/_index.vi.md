---
title : "Đăng kí SSL certificate"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2.2 </b> "
---

1. Truy cập [giao diện quản trị dịch vụ ACM](https://console.aws.amazon.com/acm/home) 
  + Click **Request a certificate**.
![ACM](/images/2.prerequisite/025-acm.png)

2. Tại màn hình **Request certificate**
  + Click **Next**.
![ACM](/images/2.prerequisite/026-acm.png)

3. Tại màn hình **Request public certificate**
  + Tại mục **Fully qualified domain name**, nhập domain của bạn.
  + Tại mục **Add another name to this certificate**, nhập ***.domain** để certificate này sẽ bảo vệ cả cho subdomain của bạn.
  ![ACM](/images/2.prerequisite/027-acm.png)
  + Cuộn xuống cuối trang, click **Request**.

4. Click vào **View certificate** vừa tạo
  + Click **Create records in Route 53**.
![ACM](/images/2.prerequisite/028-acm.png)
  + Sau khi verify, AWS sẽ tự động tạo CNAME record cho SSL vào trong hosted zone.
  ![ACM](/images/2.prerequisite/029-acm.png)
  + Kiểm tra thấy status chuyển sang trạng thái **Issued** nghĩa là bạn đã request certificate thành công.
  ![ACM](/images/2.prerequisite/030-acm.png)