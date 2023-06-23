---
title : "Kiểm tra kết quả"
date :  "`r Sys.Date()`" 
weight : 5 
chapter : false
pre : " <b> 5. </b> "
---
- Gõ địa chỉ **https://subdomain/demo-cognito/** vào trình duyệt

    (Thay subdomain tương ứng của bạn vào chỗ “subdomain” trong URL)

- Click vào **Go to dashboard**

   https://drive.google.com/file/d/13F1_owuio3eYqvFjUXHnmzpdzqd4m02a/view?usp=sharing 

- Lúc này, bạn sẽ được điều hướng đến màn hình Sign in của Cognito

{{% notice info %}}
Nếu bạn có thể vào thẳng màn hình dashboard mà không cần login thì có khả năng là do trình duyệt vẫn lưu cache. Hãy xóa cache rồi truy cập lại, hoặc dùng trình duyệt ẩn danh để đảm bảo chính xác.
{{% /notice %}}

- Nhập thông tin tài khoản mà bạn đã tạo trước đó rồi ấn Enter
![test](/images/5.test/002-login.png)
- Sau khi đăng nhập xong, bạn sẽ được điều hướng về đúng màn hình dashboard.
![test](/images/5.test/003-dashboard.png)
- Tại đây, bạn có thể thử chức năng logout bằng cách click vào **Logout**
- Sau khi logout xong, bạn vẫn có thể truy cập được vào màn hình dashboard bình thường, đó là bởi vì khi ta gọi Cognito logout endpoint, chỉ session của Cognito bị xóa, còn session của ALB thì không. Ở bước cấu hình rule cho ALB, chúng ta đã để session timeout là 180 giấy, nên bạn có thể chờ sau 3 phút kể từ khi click vào link logout rồi mới truy cập lại màn hình dashboard. Khi đó, chắc chắn bạn sẽ phải đăng nhập lại.

    Bạn có thể thấy:
- Trước khi logout, trình duyệt có 2 cookie
![test](/images/5.test/004-beforelogout.png)
- Sau khi logout, trình duyệt vẫn còn 1 cookie của ALB
![test](/images/5.test/005-afterlogout.png)
- Để có thể tự động xóa cả ALB session sau khi logout, chúng ta cần phải viết thêm xử lí ở backend nữa. Mục tiêu của bài lab này là để làm quen với cách tạo 1 website đơn giản, sửa dụng ALB và Cognito để cấu hình điều hướng, xác thực, cho nên phần xử lí backend sẽ được đề cập ở một bài lab khác.

    Chúc mừng bạn vừa hoàn thành bài thực hành. Hãy nhớ thực hiện bước dọn dẹp tài nguyên để tránh sinh chi phí ngoài ý muốn nhé.