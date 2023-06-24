---
title : "Kiểm tra kết quả"
date :  "`r Sys.Date()`" 
weight : 9
chapter : false
pre : " <b> 9. </b> "
---
- Gõ địa chỉ **https://subdomain/demo-cognito/** vào trình duyệt

    (Thay subdomain tương ứng của bạn vào chỗ “subdomain” trong URL)

- Click vào **Go to my page** rồi thực hiện login.
![DNS](/images/6.dns/004.png)
 
- Tiến hành F5 liên tục.
https://drive.google.com/file/d/13F1_owuio3eYqvFjUXHnmzpdzqd4m02a/view?usp=sharing 
- Bạn có thể thấy, dù được điều hướng luân phiên giữa 2 EC2, nhưng mỗi lần F5, visit time vẫn được tăng thêm 1, chứng tỏ chúng ta đã triển khai redis thành công. 

    Chúc mừng bạn vừa hoàn thành bài thực hành. Hãy nhớ thực hiện bước dọn dẹp tài nguyên để tránh sinh chi phí ngoài ý muốn nhé.