---
title : "Hiện trạng trước khi dùng Redis"
date :  "`r Sys.Date()`" 
weight : 7 
chapter : false
pre : " <b> 7. </b> "
---

1. Thực hiện thay đổi source code
  + Truy cập vào repo simpleHTML trong github.
  + Edit file index.html
  + Click **Commit changes**.
  ![test](/images/5.test/001.png)

2. Kiểm tra pipeline
  + Quay lại màn hình detail pipeline **demo**.
  + Ngay sau khi bạn commit thay đổi vào repo, CodePipeline sẽ nhận ra và tự động run pipeline.
  + Bạn có thể thấy, sau khi **Source** stage chạy succeeded, **Approval** stage sẽ ở trạng thái **waiting for approval**.
  ![test](/images/5.test/002.png)
  + Lúc này, bạn sẽ nhận được thông báo đến Slack.
  ![test](/images/5.test/003.png)
  + Nếu bạn click **Yes** thì sẽ bị lỗi như sau.
  ![test](/images/5.test/004.png)
  + Lí do là vì chúng ta vẫn chưa có xử lí lắng nghe kết quả approve để thực hiện action tương ứng.
  Ở bước tiếp theo, chúng ta sẽ tạo API gateway và Lambda function để xử lí approve result. API gateway sẽ nhận kết quả approve từ Slack rồi invoke Lambda function. Trường hợp được approved, Lambda sẽ gọi API đến CodePipeline để tiến hành chạy đến **deploy** stage. Nếu không thì pipeline sẽ dừng và không chạy đến **deploy** stage. (Nhớ test lại xem case no có chạy ko
  ........................à
  fajghwgjerlhtjyk
  )

