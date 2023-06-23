---
title : "Tạo target group"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 3.1. </b> "
---

1. Truy cập vào [giao diện quản trị của dịch vụ Amazon ElastiCache](https://console.aws.amazon.com/elasticache/home).
  + Mở menu **Redis clusters**.
  + Click chọn **Create Redis Cluster**.
![redis](/images/7.redis/001.png)

2. Tại màn hình tạo Redis cluster
  + Tại mục **cluster creation method**, chọn **Configure and create a new cluster**.
  + Tại mục **Cluster mode**, chọn **Disabled**.
  + Tại mục **Name**, nhập **demo-cognito**.
  ![redis](/images/7.redis/002.png)
  + Tại mục **Location**, chọn **AWS Cloud**.
  + Bỏ tick mục **Multi-AZ** (vì đây chỉ là bài lab đơn giản, không cần đến tính năng này).
  + Bỏ tick mục **Auto-failover** (vì đây chỉ là bài lab đơn giản, không cần đến tính năng này).
    ![redis](/images/7.redis/003.png)
  + Tại mục **Node type**, chọn **t2.micro**.
  + Tại mục **Number of replicas**, nhập **0**.
  + Tại mục **Subnet groups**, chọn **Create a new subnet group**.
  + Tại mục **Name**, nhập **redis-cluster-subnet**.
  + Tại mục **VPC ID**, chọn **Demo-vpc**.
   ![redis](/images/7.redis/004.png)
  + Tại mục **Manage subnets**, tick chọn 2 private subnet trong demo VPC, rồi click **Choose**.
  ![redis](/images/7.redis/005.png)
  + Click button **Next** ở cuối trang.
  + Đến màn hình của **step 2: Advanced settings**, tiếp tục scroll xuống cuối trang rồi click **Next**.
  + Đến màn hình của **step 3: Review and create**, kiểm tra lại thông tin, nếu không có vấn đề gì thì  scroll xuống cuối trang rồi click **Create**.
    ![redis](/images/7.redis/006.png)

3. Tại màn hình detail của Redis cluster
  + Sau khi tạo Redis cluster thành công, bạn hãy vào màn hình detail và copy thông tin **Primary endpoint**.
  ![redis](/images/7.redis/007.png)
 