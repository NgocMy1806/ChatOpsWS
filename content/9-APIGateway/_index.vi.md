---
title : "Tạo API gateway"
date :  "`r Sys.Date()`" 
weight : 9
chapter : false
pre : " <b> 9. </b> "
---
1.  Truy cập vào [giao diện quản trị của dịch vụ API Gateway](https://us-east-1.console.aws.amazon.com/apigateway)
  + Click **Create API**
  ![api](/images/apigateway/001.png)
  + Chọn type **HTTP API**
  ![api](/images/apigateway/002.png)
2. Tại màn hình **Create an API**
  + Tại mục **Integrations**, chọn **Lambda**.
  + Tại mục **Lambda function**, chọn **handleResult**.
  + Tại mục **API name**, nhập **InteractiveButtonHandler**.
  ![api](/images/apigateway/003.png)

3. Tại màn hình **Configure routes**
  + Tại mục **Method**, chọn **POST**.
  + Click **Next**
  ![api](/images/apigateway/004.png)

4. Tại màn hình **Define stages**
  + Giữ nguyên setting default, click **Next**.

5. Tại màn hình **Review and create**
  + Kiểm tra lại thông tin, click **Save**.

6. Lấy thông tin cần thiết
  + Truy cập vào màn hình details của API vừa tạo, lưu lại thông tin **invoke URL**.
  ![api](/images/apigateway/005.png)
  + Truy cập vào mục **Routes**, lưu lại thông tin routes của POST API.
  ![api](/images/apigateway/006.png)