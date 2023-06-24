---
title : "Apply redis cho application"
date :  "`r Sys.Date()`" 
weight : 7
chapter : false
pre : " <b> 7.2. </b> "
---
#### Cấu hình file .env và cài predis package
+ Open source code đã giải nén ban nãy bằng IDE như Visual Studio Code, PHP Storm,…
+ Sửa các env liên quan đến session, redis như sau:
```
CACHE_DRIVER=redis
SESSION_DRIVER=redis
REDIS_HOST=primary endpoint of redis cluster
REDIS_CLIENT=predis
```
  ![redis](/images/7.redis/008.png)
+ Sau đó, mở terminal, chạy command `composer require predis/predis` để cài đặt  predis package.
  {{% notice info %}}
  Predis là một thư viện PHP được sử dụng để làm việc với Redis, một hệ thống cơ sở dữ liệu key-value cache in-memory nhanh chóng và mạnh mẽ. Predis cung cấp một giao diện dễ sử dụng cho việc kết nối và tương tác với Redis từ ứng dụng PHP của bạn.
  {{% /notice %}}
![redis](/images/7.redis/009.png)
+ Nén folder cognito-redis lại lần nữa.

#### Deploy new version 
+ Truy cập vào màn hình detail của EB enviroment đã tạo.
+ Click **Upload and deploy**.
![redis](/images/7.redis/010.png)
+ Tại popup **Upload and deploy**, upload folder cognito-redis vừa nén lên.
+ Tại mục **Version label**, nhập v1.1.
+ Click **Deploy**.
![redis](/images/7.redis/011.png)
