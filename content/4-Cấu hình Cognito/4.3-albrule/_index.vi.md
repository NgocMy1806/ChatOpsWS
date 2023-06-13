---
title : "ALB Authentication rule"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 4.3. </b> "
---
1. Mở màn hình quản lí Load balancer, click chọn **demo-cognito**
 ![Cognito](/images/4.cognito/017-alb-cognito.png)
- Tick vào listener **HTTPS:443**, rồi click **Manage rules**
 ![Cognito](/images/4.cognito/018-alb-cognito.png)
- Click vào dấu `+` để tạo rule mới
 ![Cognito](/images/4.cognito/019-alb-cognito.png)
- Mục đích của chúng ta là cấu hình để khi user truy cập vào trang web có path là `/demo-cognito/dashboard.html`, ALB sẽ điều hướng tới Cognito để thực hiện xác thực. Sau khi xác thực xong, ALB sẽ cho user truy cập vào trang web yêu cầu nằm trong EC2. Để thực hiện được việc này, chúng ta sẽ cấu hình như sau:
- Click vào **Add condition**, chọn **Path**
- Tại ô **Path**, nhập **/demo-cognito/dashboard.html**
- Click vào **Add action**, chọn **Authenticate…**
- Tại mục **Authenticate,** chọn **Amazon Cognito**.
- Tại mục **Cognito user pool,** chọn ID của user pool demo-cognito.
- Tại mục **App client,** chọn ID của app client **demo cognito**.
- Tại mục **Session timeout**, nhập 180
{{% notice info %}}
Bạn có thể để nguyên giá trị Session timeout mặc định cũng được. Việc thay đổi thành 180s này chỉ nhằm mục đích test nhanh hơn. Lí do sẽ được giải thích chi tiết hơn ở Mục 5. `Kiểm tra kết quả`
{{% /notice %}}

 ![Cognito](/images/4.cognito/020-alb-cognito.png)

- Click vào dấu `✔ ` để hoàn thành việc tạo action điều hướng tới Cognito
- Tiếp tục click vào **Add action,**  chọn **Forward to**
 ![Cognito](/images/4.cognito/021-alb-cognito.png)
- Tại mục **Target group**, chọn **demo-cognito**
- Click vào dấu  `✔ ` để hoàn thành việc tạo action điều hướng tới target group sau khi user đã thực hiện xác thực bằng Cognito.
- Click vào **Save** để lưu nội dung cấu hình của Rule
 ![Cognito](/images/4.cognito/022-alb-cognito.png)

    Vậy là chúng ta đã hoàn thành xong việc cấu hình ALB và Cognito.



