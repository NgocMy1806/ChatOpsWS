---
title : "Tạo domain"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 2.1 </b> "
---
Route 53 là dịch vụ DNS của AWS. Nó cung cấp hai dịch vụ chính là DNS và đăng ký tên miền. Để thực hiện bài lab này, bạn cần chuẩn bị một tên miền đã có SSL certificate. 
Bạn có thể đăng ký tên miền trên Route 53 hoặc đăng ký từ nhà cung cấp khác như GoDaddy, Freenom, vv. rồi chuyển dịch vụ DNS về Route 53.

Vì Route 53 không phải là nội dung chính của bài lab này, tôi sẽ chỉ giới thiệu nhanh các bước cơ bản để chuyển DNS service từ nhà cung cấp tên miền khác về Route 53, chứ không mô tả, giải thích chi tiết.

- Bước 1: Đăng ký tên miền trên nhà cung cấp tên miền như GoDaddy, Freenom, ...
- Bước 2: Tạo public hosted zone trên Route 53. Đặt tên hosted zone trùng với tên miền.
- Bước 3: Sau khi tạo xong hosted zone, bạn sẽ có 4 NS record. Sao chép 4 NS record này, sau đó truy cập màn hình quản lý Nameserver trong nhà cung cấp tên miền và thay đổi các NS record mặc định thành 4 NS record của hosted zone trên Route 53.
- Bước 4: Việc thay đổi nameserver có thể mất khoảng vài phút đến 24 giờ. Bạn có thể kiểm tra xem NS record đã được cập nhật chưa bằng cách mở command prompt, sau đó nhập lệnh `nslookup -q=ns {{domain}}`.
![DNS](/images/2.prerequisite/031-nslookup.png)

Bạn có thể tham khảo cách làm từ video sau: https://www.youtube.com/watch?v=L8YTHHweR3M&t=231s 

Sau khi đã cập nhật NS records thành công, bạn hãy chuyển sang bước tiếp theo để tiến hành đăng kí SSL certificate cho domain.

