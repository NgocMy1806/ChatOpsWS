---
title : "Add Approval stage"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 6. </b> "
---


  In this step, we will add the Approval stage to the pipeline, and configure it so that when the pipeline reaches this stage, it will send a notification to SNS. SNS will then invoke the Lambda function sendApproveRequest to send the approval request to the selected Slack channel.

1. Access [CodePipeline management console](https://us-east-1.console.aws.amazon.com/codesuite/codepipeline/pipelines)
  + Click **demo** pipeline.

2. On detail screen of **demo** pipeline, proceed to add **Approval stage**
  + Click button **Edit**
  ![pipeline](/images/pipeline/010.png)
  + Click the **Add stage** button below the **Source** stage.
  ![pipeline](/images/pipeline/011.png)
  + For **Stage name**, enter **Approval**.
  + Click **Add stage**.
  ![pipeline](/images/pipeline/012.png)
  + Click **Add action group**.
  ![pipeline](/images/pipeline/013.png)
  + For **Action name**, enter **ApprovalOrDeny**.
  + For **Action provider**, select **Manual approval**.
  + For **SNS topic ARN**, select topic **demo**.
  + Click **Done**.
  ![pipeline](/images/pipeline/014-1.png)
  + Click **Save**.
  ![pipeline](/images/pipeline/015.png)

