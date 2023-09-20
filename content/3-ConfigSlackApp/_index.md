---
title : "Config Slack App"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b>3.</b> "
---

1. Create Slack app
  + Access link https://api.slack.com/apps , click button **Create new app**.
  (If you don't have a workspace, please create one on Slack with your email first.)
  + Select **From scratch**.
  ![slack](/images/slack/001.png)
  + For **App name**, enter **demo**.
  + For **Workspace**, select the workspace you want to use for this lab.
  + Click **Create app**.
  ![slack](/images/slack/002.png)

2. Create webhook
  + Open the Slack app on your PC and create channel **test-noti**. This channel will be used to receive notifications from Lambda when the pipeline reaches the **need approval** stage.
  ![slack](/images/slack/004.png)
  + On **Basic Information** screen, click **Incoming Webhook**.
  ![slack](/images/slack/003.png)
  + On **Incoming Webhooks** screen, activate the webhook by clicking the OFF button so it switches to the ON state.
  + Click **Add New Webhook to Workspace**
  ![slack](/images/slack/005.png)
  + Allow the demo app to access the newly created **test-noti** channel.
  + Click **Allow**.
  ![slack](/images/slack/006.png)
  + After granting permission, you will see a webhook created. You will use this webhook when creating a Lambda function.
  ![slack](/images/slack/007.png)

