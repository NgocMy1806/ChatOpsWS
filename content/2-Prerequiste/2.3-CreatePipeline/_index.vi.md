---
title : "Tạo pipeline"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b>4</b> "
---

1.  Truy cập vào [giao diện quản trị của dịch vụ CodePipeline](https://us-east-1.console.aws.amazon.com/codesuite/codepipeline/pipelines).
  + Click **Create Pipeline**.
  ![pipeline](/images/pipeline/000.png)

2. Tại màn hình **Choose pipeline settings**
  + Tại mục **Pipeline name**, nhập **demo**.
  + Click **Next**.
  ![pipeline](/images/pipeline/001.png)

3. Tại màn hình **Add source stage**
  + Tại mục **Source provider**, chọn **GitHub (version 2)**.
  + Tại mục **Connection**, click **Connect to GitHub**.
  ![pipeline](/images/pipeline/002.png)

  + Tại mục **Connection name**, nhập **demo**.
  + Click button **Connect to Github**.
  ![pipeline](/images/pipeline/003.png)
  + Click button **Install a new app**.
  + Tiến hành login vào github.
  + Tại màn hình **Install AWS Connector for GitHub page**, click **Select repositories** và chọn repo **simpleHTML** đã tạo ban nãy.
  ![pipeline](/images/pipeline/004.png)
  + Click button **Save**.
  + Sau đó, bạn sẽ được redirect về màn hình **Connect to Github**.
  + Click button **Connect** để hoàn thành việc kêt nối đến Github.
  ![pipeline](/images/pipeline/005.png)
  + Sau đó, bạn sẽ được redirect về màn hình **Add source stage**.
  + Lúc này, trạng thái connection đã đổi sang **ready**.
  + Tại mục **Repository name**, chọn repo **simpleHTML**.
  + Tại mục **Branch name**, chọn **main**.
  + Click button **Next**.
  ![pipeline](/images/pipeline/006.png)

4. Tại màn hình **Add build stage**
  + Click **Skip build stage**.
  ![pipeline](/images/pipeline/008.png)

5. Tại màn hình **Add deploy stage**
  + Tại mục **Deploy provider**, chọn **AWS Elastic Beanstalk**.
  + Tại mục **Application name**, chọn **demo**.
  + Tại mục **Environment name**, chọn **demo**.
  + Click **Next**.
  ![pipeline](/images/pipeline/009.png)

6. Tại màn hình **Review**
  + Kiểm tra lại thông tin.
  + Scroll xuống cuối trang, click **Create pipeline**.