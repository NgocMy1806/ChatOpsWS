---
title : "Kiểm tra kết quả"
date :  "`r Sys.Date()`" 
weight : 11 
chapter : false
pre : " <b> 11. </b> "
---

1. Thực hiện thay đổi source code
  + Truy cập vào repo simpleHTML trong github.
  + Edit file index.html
  + Click **Commit changes**.
  ![test](/images/5.test/005.png)

2. Kiểm tra pipeline trong trường hợp "approve"
  + Quay lại màn hình detail pipeline **demo**.
  + Ngay sau khi bạn commit thay đổi vào repo, CodePipeline sẽ nhận ra và tự động run pipeline.
  + Bạn có thể thấy, sau khi **Source** stage chạy succeeded, **Approval** stage sẽ ở trạng thái **waiting for approval**.
  ![test](/images/5.test/002.png)
  + Lúc này, bạn sẽ nhận được thông báo đến Slack.
  ![test](/images/5.test/006.png)
  + Nếu bạn click **Yes** thì message sẽ đổi thành "Starting to deploy**.
  ![test](/images/5.test/006-1.png)
  + Quay lại màn hình detail của pipeline **demo**, bạn sẽ thấy pipeline đã chạy đến **deploy** stage.
  ![test](/images/5.test/007.png)
  + Sau khoảng 3 phút là deploy thành công. 
  ![test](/images/5.test/008.png)
  + Thử truy cập vào domain của EB enviroment, bạn sẽ kiểm tra được xem quá trình deploy đã thành công thật chưa.
  ![test](/images/5.test/009.png)
  
3. Kiểm tra pipeline trong trường hợp "reject"
  + Thay đổi source code lại 1 lần nữa
  ![test](/images/5.test/009-1.png)
  + Khi noti slack đến, hãy click **No**. Lúc này, màn hình sẽ show mesage "Rejected successfully".
  ![test](/images/5.test/010-1.png)
  + Quay lại màn hình detail của pipeline **demo**, bạn sẽ thấy **Approval** stage chuyển sang trạng thái **failed**.
  ![test](/images/5.test/010.png)
  +  Thử truy cập vào domain của EB enviroment, site vẫn hiển thị nội dung của commit lần trước, chứ không deploy commit mới.
  ![test](/images/5.test/009.png)

  Chúc mừng bạn vừa hoàn thành bài thực hành. Hãy nhớ thực hiện bước dọn dẹp tài nguyên để tránh sinh chi phí ngoài ý muốn nhé.
