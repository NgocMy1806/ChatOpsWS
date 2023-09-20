---
title : "Cấu hình Slack App"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b>3.</b> "
---

1. Tạo Slack app
  + Truy cập vào link https://api.slack.com/apps , ấn button **Create new app**.
  (nếu chưa có workspace thì bạn hãy tự tạo 1 workspace trên Slack bằng email của bạn trước nhé.)
  + Chọn **From scratch**.
  ![slack](/images/slack/001.png)
  + Tại mục **App name**, nhập **demo**.
  + Tại mục **Workspace**, chọn workspace bạn muốn dùng để thực hành trong bài lab này.
  + Click **Create app**.
  ![slack](/images/slack/002.png)

2. Tạo webhook
  + Mở app Slack trên PC và tạo channel **test-noti**. Channel này sẽ được dùng để nhận thông báo từ Lambda khi pipeline chạy đến stage **need approve**. 
  ![slack](/images/slack/004.png)
  + Tại màn hình **Basic Information**, click **Incoming Webhook**.
  ![slack](/images/slack/003.png)
  + Tại màn hình **Incoming Webhooks**, active webhook bằng cách click vào button OFF để nó chuyển sang trạng thái ON.
  + Click **Add New Webhook to Workspace**
  ![slack](/images/slack/005.png)
  + Cho app demo được phép truy cập vào channel **test-noti** vừa tạo.
  + Click **Allow**.
  ![slack](/images/slack/006.png)
  + Sau khi cấp quyền xong, bạn sẽ thấy 1 webhook được tạo ra. Bạn sẽ dùng webhook này khi tạo Lambda function.
  ![slack](/images/slack/007.png)

