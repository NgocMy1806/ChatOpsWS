---
title : "Tạo website trên EC2"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 2.6</b> "
---

1. Truy cập vào EC2 vừa tạo

    Bài lab này sẽ dùng EC2 instance connect để truy cập vào EC2
+ Tick vào instance vừa tạo
+ Click **Connect**.
![EC2](/images/2.prerequisite/014-ec2connect.png)
![EC2](/images/2.prerequisite/015-ec2connect.png)

2. Cài đặt Apache web server trên EC2

    Để đảm bảo rằng tất cả các gói phần mềm của bạn đều được cập nhật, ta thực hiện lệnh sau:
    ```
    sudo yum update -y
    ```
    ![EC2](/images/2.prerequisite/017-yumpdate.png)

    Chạy lệnh sau để cài đặt Apache
    ```
    sudo yum install -y httpd
    ```
    ![EC2](/images/2.prerequisite/018-installhttpd.png)

    Khởi động Apache 
    ```
    sudo systemctl start httpd
    ```

    Sử dụng lệnh systemctl để cấu hình máy chủ web Apache khởi động mỗi lần khởi động hệ thống.
    ```
    sudo systemctl enable httpd
    ```

    Bạn có thể xác minh rằng httpd đang bật bằng cách chạy lệnh sau:
    ```
    sudo systemctl is-enabled httpd

    ```
    ![EC2](/images/2.prerequisite/019-starthttpd.png)

3. Tạo website trên EC2

      Tiếp theo chúng ta sẽ tiến hành tạo 1 website đơn giản có 3 page, trong đó page index và page logged out là page public, tất cả mọi người đều có thể truy cập, còn page dashboard là page private, chỉ user đã đăng nhập mới có thể xem.

    Dưới đây là chi tiết các bước tạo website:
  + Điều hướng đến thư mục **/var/www/html** bằng lệnh `cd /var/www/html`.
  + Tạo 1 folder tên **demo-cognito** bằng lệnh `sudo mkdir demo-cognito`.
  + Điều hướng đến thư mục **demo-cognito** bằng lệnh `cd demo-cognito`.
![EC2](/images/2.prerequisite/020-mkdir.png)
  + Tạo file index.html bằng lệnh `sudo nano index.html`. Nhập nội dung sau cho file index:
    ```
    <html>
      <body>
        <h1>Welcome to the demo-cognito website</h1>
        <p>This is the index page</p>
        <a href="dashboard.html">Go to dashboard</a>
      </body>
    </html>
    ```
     ![EC2](/images/2.prerequisite/021-index.png)
  Lưu nội dung file bằng cách ấn tổ hợp phím Ctrl+X, sau đó ấn Y, rồi ấn Enter.

  + Tạo file dasboard.html bằng lệnh `sudo nano dashboard.html`. Nhập nội dung sau cho file dashboard:
    ```
    <html>
      <body>
        <h1>Congratulations!</h1>
        <p>You are logged in. This is dashboard page</p>
        <a href="logged_out.html">Logout</a>
      </body>
    </html>
    ```
    ![EC2](/images/2.prerequisite/022-dashboard.png)
  Lưu nội dung file bằng cách ấn tổ hợp phím Ctrl+X, sau đó ấn Y, rồi ấn Enter.

  + Tạo file logged_out.html bằng lệnh `sudo nano logged_out.html`. Nhập nội dung sau cho file logged_out:
    ```
    <html>
      <body>
        <h1>You are logged out</h1>
        <p>Goodbye!</p>
        <a href="index.html">Return to home page</a>
      </body>
    </html>
    ```
    ![EC2](/images/2.prerequisite/023-logged_out.png)
  Lưu nội dung file bằng cách ấn tổ hợp phím Ctrl+X, sau đó ấn Y, rồi ấn Enter.

  + Sau khi đã tạo xong các file, tiến hành khởi động lại Apache web server bằng lệnh `sudo service httpd restart`.
  ![EC2](/images/2.prerequisite/024-restarthttpd.png)


    Vậy là bạn đã hoàn thành tạo 1 website đơn giản trên EC2.



