---
title : "Test send noti"
date :  "`r Sys.Date()`" 
weight : 7 
chapter : false
pre : " <b> 7. </b> "
---

1. Make changes to the source code
  + Access the **simpleHTML** repo in github.
  + Edit file index.html
  + Click **Commit changes**.
  ![test](/images/5.test/001-1.png)

2. Test pipeline
  + Return to the detailed screen of **demo** pipeline.
  + After you commit changes to the repo, CodePipeline will recognize and automatically run the pipeline.
  + You can see, after the **Source** stage runs succeeded, the **Approval** stage will be in **waiting for approval** state.
  ![test](/images/5.test/002.png)
  + At this point, you will receive a notification to Slack.
  ![test](/images/5.test/003.png)
  + If you click **Yes**, you will get the following error.
  ![test](/images/5.test/004.png)
  + The reason is because we don't have a handle to listen to the approval results to perform the corresponding action.
  In the next step, we will create an API gateway and Lambda function to handle the approval result. The API gateway will receive approval results from Slack and then invoke the Lambda function. If approved, Lambda will call the API to CodePipeline to proceed to the **deploy** stage. Otherwise the pipeline will stop and not run to the **deploy** stage.
