---
title : "Dọn dẹp tài nguyên  "
date : 2023
weight : 10
chapter : false
pre : "<b> 10. </b>"
---

Chúng ta sẽ tiến hành các bước sau để xóa các tài nguyên chúng ta đã tạo trong bài thực hành này.

### Xóa EB enviroment:

- Truy cập **Elastic Beanstalk Management Console**
- Mở menu **Enviroment**, tick vào enviroment đã tạo trong bài lab, click button **Action** rồi chọn **Terminate enviroment**. 

### Xóa Security group

1. Truy cập vào **EC2**
2. Chọn **Security Group**
3. Chọn các security group liên quan đến bài lab
4. Chọn **Actions**
5. Chọn **Delete security group**

### Xóa Keypair

1. Truy cập **EC2**
2. Chọn **Key Pairs**
3. Chọn **Actions**
4. Chọn **Delete**

#### Xóa User pool

1. Truy cập Cognito
2. Chọn User pool
3. Chọn **Delete**

#### Xóa VPC

1. Truy cập **VPC**
2. Chọn **Your VPCs**
3. Chọn các vpc liên quan bài lab
4. Chọn **Actions**
5. Chọn **Delete VPC**


#### Xóa Certificates 

1. Truy cập **ACM**
2. Chọn **List certificates**
3. Chọn certificate liên quan đến bài lab
4. Chọn **Delete**

#### Xóa Hosted zone 

1. Truy cập **Route 53** 
2. Chọn **Hosted zone**
3. Chọn Hosted zone liên quan đến bài lab
4. Chọn **Delete**