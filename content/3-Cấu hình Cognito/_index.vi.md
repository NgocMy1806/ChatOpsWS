---
title : "Cấu hình Cognito"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 3. </b> "
---


  Ở bước này, chúng ta sẽ tiến hành cấu hình Amazon Cognito.

1. Truy cập vào [giao diện quản trị của dịch vụ Amazon Cognito](https://console.aws.amazon.com/cognito/v2/home).
  + Click chọn **User pools**.
  + Click chọn **Create user pools**.
![Cognito](/images/4.cognito/001-userpool.png)

2. Tại màn hình **Configure sign-in experience**
  + Tại mục **Cognito user pool sign-in options**, chọn **Email**.
  + Click **Next**.
![Cognito](/images/4.cognito/002-userpool.png)

3. Tại màn hình **Configure security requirements**
  + Tại mục **Password policy mode**, chọn **Custom**.
  + Bỏ tick tất cả các mục **Password requirements**.

  {{% notice info %}}
  Bạn có thể để nguyên mode **Cognito defaults** cũng được, tuy nhiên, để khỏi mất thời gian tạo mật khẩu phức tạp, bài lab này sẽ làm theo hướng dùng Custom policy
  {{% /notice %}}
      ![Cognito](/images/4.cognito/003-userpool.png)
  + Tại mục **MFA enforcement**, chọn **No MFA**.
  + Click **Next**.
![Cognito](/images/4.cognito/004-userpool.png)

4. Tại màn hình **Configure sign-in experience**
  + Không thực hiện thay đổi nào hết
  + Click **Next**.


5. Tại màn hình **Configure message delivery**
  + Tại mục **Email provider**, chọn **Send email with Cognito**.
  + Click **Next**.
![Cognito](/images/4.cognito/005-userpool.png)

6. Tại màn hình **Integrate your app**
  + Tại mục **User pool name**, điền **demo-cognito**.
  + Tại mục **Hosted authentication pages**, tick vào **Use the Cognito Hosted UI**.
  ![Cognito](/images/4.cognito/006-userpool.png)

  + Tại mục **Domain type**, chọn **Use a Cognito domain**.
  + Tại mục **Cognito domain**, nhập domain prefix bạn muốn. 
  + Tại mục **App type**, chọn **Public client**.
  + Tại mục **App client name**, nhập **demo-cognito**.
  ![Cognito](/images/4.cognito/007-userpool.png)
  + Tại mục **Client secret**, chọn **Generate a client secret**.
  + Tại mục **Allowed callback URLs**, nhập **domain/oauth2/idpresponse**.
  {{% notice info %}}
  Thay domain bạn dự kiến dùng vào chữ `domain` trong URL phía trên
  {{% /notice %}}
![Cognito](/images/4.cognito/008-userpool.png)
  + Mở rộng phần **Advanced app client settings**
  + Kéo xuống đến mục **Allowed sign-out URLs**, nhập **domain/index**
  {{% notice info %}}
  Thay domain bạn dự kiến dùng vào chữ `domain` trong URL phía trên
  {{% /notice %}}
  + Tại mục **OpenID Connect scopes**, chỉ chọn **OpenID**. Lí do là vì nếu bạn chọn cả **Phone** và **Email** thì bạn sẽ không thể lấy các thông tin khác của user, ví dụ như username.
  + Scroll xuống cuối trang, click **Next**.
![Cognito](/images/4.cognito/009-userpool.png)

7. Tại màn hình **Review and create**

    Kiểm tra lại thông tin rồi ấn **Create user pool**.
  ![Cognito](/images/4.cognito/010-userpool.png)

8. Hoàn thành tạo User pool

  Bạn hãy lưu lại các thông tin sau để lát nữa chúng ta sẽ tiến hành config file .env cho application.
  ```
  COGNITO_CLIENT_ID
  COGNITO_CLIENT_SECRET
  COGNITO_DOMAIN
  COGNITO_LOGOUT_REDIRECT_URI
  ````

