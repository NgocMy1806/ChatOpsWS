---
title : "Cấu hình ALB"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

#### Config rule cho port 80
1. Truy cập vào [giao diện quản trị của dịch vụ EC2](https://console.aws.amazon.com/ec2/v2/home).
  + Click chọn **Load balancer**.
  + Click chọn ALB vừa được tạo bởi EB.
  + Mở tab **Listener**.
  + Tick vào listener **HTTP:80**, rồi click **Manage rules**.
![ALB](/images/3.alb/005-alb.png)

    Tại màn hình manage rule cho listener **HTTP:80**, chúng ta sẽ tiến hành setting redirect tất cả traffic từ port 80 vào 443 để đảm bảo security. 
  + Click icon **pen** để tiến hành edit rule.
  + Click icon **trash** để xóa action hiện tại, không cho phép traffic vào port 80 của ALB được forward thẳng vào target group.
![ALB](/images/3.alb/006-alb.png)
  + Click **Add action** để tạo action mới, rồi click **Redirect to...**.
![ALB](/images/3.alb/007-alb.png)

  + Tại dropdown **protocol**, chọn **HTTPS**.
  + Tại field **port**, nhập **443**.
  + Click icon dấu tick.
  + Click button **Update**.
![ALB](/images/3.alb/008-alb.png)

#### Config rule cho port 443
  Tiếp theo, chúng ta sẽ tiến hành config rule cho port 443 của ALB, để khi user truy cập vào trang dashboard thì sẽ yêu cầu user thực hiện đăng nhập bằng Amazon Cognito, nếu user truy cập vào trang index thì sẽ forward thẳng tới target group.
  + Trước hết, bạn hãy truy cập vào màn hình details của ALB vừa được tạo.
  + Mở tab **Listener**.
  + Tick vào listener **HTTP:443**, rồi click **Manage rules**.

![ALB](/images/3.alb/009-alb.png)
  + Click icon **plus** rồi click **Insert rule**. 

![ALB](/images/3.alb/010-alb.png)
  + Tại ô condition, chọn **Path**, rồi nhập **/dashboard**.
  + Click **Add Action**, rồi chọn **Authenticate**.
![ALB](/images/3.alb/011-alb.png)
  + Tại mục **Cognito user pool**, chọn ID của user pool đã tạo.
  + Tại mục **App client**, chọn app tương ứng của user pool.
  + Click icon dấu tick.
![ALB](/images/3.alb/012-alb.png)
  + Tiếp tục click **Add action**, rồi click **Forward to...**.
![ALB](/images/3.alb/013-alb.png)
  + Tại mục **target group**, chọn target group vừa được EB tạo.
  + Click icon dấu tick.
  + Click button **Save**.
  ![ALB](/images/3.alb/014-alb.png)


      


