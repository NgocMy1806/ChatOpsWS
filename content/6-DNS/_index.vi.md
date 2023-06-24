---
title : "Cấu hình DNS record"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 6. </b> "
---


 Ở bước này, chúng ta sẽ tiến hành cấu hình route 53 để khi truy cập vào domain democognito.mymy.asia thì DNS server sẽ trỏ tới domain của EB.
  + Truy cập vào [giao diện quản trị của dịch vụ Route53](https://console.aws.amazon.com/route53/v2/home).
  + Click chọn **Hosted zones**.
  + Click vào tên Hostes zone đã tạo
![DNS](/images/6.dns/001.png)
  + Click vào **Create record**
  ![DNS](/images/6.dns/002.png)
  + Tại mục **Record name**, nhập **democognito**.
  {{% notice info %}}
  Nếu bạn muốn trỏ thẳng domain chính đến EB enviroment thì có thể bỏ trống mục này
  {{% /notice %}}
  + Bật toggle **Alias**.
  + Chọn route traffic to **Alias to EB enviroment** ở region **us-east-1**, và chọn EB enviroment đã tạo.
  + Click **Create records**
  ![DNS](/images/6.dns/003.png)

    Sau khi tạo record thành công, bạn hãy thử truy cập bằng cách dán **record name** của record vừa tạo vào trình duyệt. 
    Lúc này bạn sẽ thấy trình duyệt hiển thị màn hình index của application.
     ![DNS](/images/6.dns/004.png)
 
