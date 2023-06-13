---
title : "Thử tạo tài khoản"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 4.2. </b> "
---
+ Click chọn user pool vừa tạo

  ![Cognito](/images/4.cognito/011-testlogin.png)

+ Mở tab App intergration

  ![Cognito](/images/4.cognito/012-testlogin.png)

+ Kéo xuống đến mục **App client list**
+ Click vào app client **demo-cognito**
  ![Cognito](/images/4.cognito/013-testlogin.png)

+ Kéo xuống đến mục ****Hosted UI****
+ Click vào **View hosted UI**
  ![Cognito](/images/4.cognito/014-testlogin.png)
Lúc này, màn hình đăng kí tài khoản của Cognito sẽ hiển thị.
Vì chúng ta chưa có tài khoản nào, nên chúng ta sẽ thử đăng kí tài khoản bằng cách click vào **Sign up**
  ![Cognito](/images/4.cognito/015-testlogin.png)

  Sau khi sign up xong, bạn sẽ bị chuyển đến màn hình báo lỗi **Not found**
  ![Cognito](/images/4.cognito/016-testlogin.png)

  Lí do là vì chúng ta chưa cấu hình ALB trỏ đến cognito.
  Chúng ta sẽ thực hiện xử lí này ở bước tiếp theo



