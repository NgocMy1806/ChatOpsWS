+++
title = "Dọn dẹp tài nguyên  "
date = 2021
weight = 6
chapter = false
pre = "<b>6. </b>"
+++

Chúng ta sẽ tiến hành các bước sau để xóa các tài nguyên chúng ta đã tạo trong bài thực hành này.

### Xóa Load Balancer:

- Truy cập **EC2 Management Console**
- Trên thanh điều hướng bên trái, chọn **Load Balancers**
- Chọn **Load Balancer** liên quan tới bài lab.
- Click **Actions**.
- Click **Delete**.

### Xóa Target Group:

- Truy cập **EC2 Management **Console**
- Trên thanh điều hướng bên trái, chọn **Target Groups**
- Chọn **Target Group** liên quan *tới bài lab.
- Click **Actions**.
- Click **Delete**.
- Click **Yes, delete**

### Xóa instance

1. Truy cập vào **EC2**
2. Chọn **Instances**
3. Chọn các instance liên quan bài lab
4. Chọn **Instance state**
5. Chọn **Terminate instance**

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