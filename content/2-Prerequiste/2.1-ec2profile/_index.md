---
title : "Create instance profile"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 2.1</b> "
---

1. Truy cập [giao diện quản trị dịch vụ IAM](https://console.aws.amazon.com/iamv2/home) để tạo instance role
  + Click **Roles**.
  + Click **Create role**.
  
![role](/images/2.prerequisite/ec2profile/001.png)

2. Tại màn hình **Create role**
  + Chọn **Trusted entity type** là **AWS service** 
  + Chọn **Use case** là **EC2**.

![role](/images/2.prerequisite/ec2profile/002.png)


  + Chọn policy **AWSElasticBeanstalkWebTier**.
![role](/images/2.prerequisite/ec2profile/003-1.png)  
  + Click **Next**.

  + Tại mục **Role name**, nhập **WebAppRole**.
  + Scroll xuống cuối màn hình, click **Create role**.

![role](/images/2.prerequisite/ec2profile/004.png)  

