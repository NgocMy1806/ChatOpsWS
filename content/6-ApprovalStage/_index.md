---
title : "Add Approval stage"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 6. </b> "
---


  Ở bước này, chúng ta sẽ tiến hành bổ sung Approval stage vào pipeline, và cấu hình để khi pipeline chạy đến stage này sẽ gửi thông báo đến SNS. Khi đó SNS sẽ invoke Lambda function sendApproveRequest để gửi request approve đến channel Slack đã chọn.

1. Truy cập vào [giao diện quản trị của dịch vụ CodePipeline](https://us-east-1.console.aws.amazon.com/codesuite/codepipeline/pipelines)
  + Click vào tên pipeline **demo** đã tạo.

2. Tại màn hình detail của pipeline **demo**
  
    2.1. Thêm **Approval stage**
  + Click button **Edit**
  ![pipeline](/images/pipeline/010.png)
  + Click button **Add stage** ở dưới stage **Source**.
  ![pipeline](/images/pipeline/011.png)
  + Tại mục **Stage name**, nhập **Approval**.
  + Click **Add stage**.
  ![pipeline](/images/pipeline/012.png)
  + Click **Add action group**.
  ![pipeline](/images/pipeline/013.png)
  + Tại mục **Action name**, nhập **ApprovalOrDeny**.
  + Tại mục **Action provider**, chọn **Manual approval**.
  + Tại mục **SNS topic ARN**, chọn topic **demo**.
  + Click **Done**.
  ![pipeline](/images/pipeline/014-1.png)
  + Click **Save**.
  ![pipeline](/images/pipeline/015.png)

