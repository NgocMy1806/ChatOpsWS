---
title : "Hiện trạng trước khi dùng Redis"
date :  "`r Sys.Date()`" 
weight : 7 
chapter : false
pre : " <b> 7. </b> "
---
- Gõ địa chỉ **https://subdomain/demo-cognito/** vào trình duyệt

    (Thay subdomain tương ứng của bạn vào chỗ “subdomain” trong URL)

- Click vào **Go to my page**
 ![DNS](/images/6.dns/004.png)

- Lúc này, bạn sẽ được điều hướng đến màn hình Sign in của Cognito. Nếu bạn chưa có account, hãy click vào text link **Sign up**, tiến hành đăng kí, rồi thực hiện login.
![test](/images/5.test/002-login.png)
- Sau khi đăng nhập xong, bạn sẽ được điều hướng về đúng màn hình dashboard.
Hãy chú ý đến thông tin **EC2 ID** và số lần **visit page**.
- Tiến hành F5 liên tục, bạn sẽ thấy nếu bạn đang ở EC2-1, lần F5 tiếp theo, nếu bạn vẫn được điều hướng vào EC2-1, thì số lần **visit page** sẽ tăng tịnh tiến thêm 1 đơn vị. Tuy nhiên, nếu lần F5 tiếp theo, bạn được điều hướng sang EC2-2, thì số lần **visit page** sẽ bị đếm lại từ 1.
![test](/images/5.test/1.png)
![test](/images/5.test/2.png)
- Lí do là bởi vì mặc định, application của chúng ta sẽ sử dụng session driver và cache driver là **file**, nghĩa là sẽ lưu trực tiếp trên server. Do đó, session trên 2 EC2 hoàn toàn không liên quan đến nhau, nên khi chúng ta được điều hướng sang EC2-2, hệ thống sẽ start 1 session mới, chứ không update vào session hiện có.
    Để xử lí vấn đề này, chúng ta sẽ sử dụng Amazon ElastiCache Redis của AWS để lưu chung session của các server vào chung 1 redis cluster. 


