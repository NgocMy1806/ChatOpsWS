---
title : "Test"
date :  "`r Sys.Date()`" 
weight : 11 
chapter : false
pre : " <b> 11. </b> "
---

1. Make changes to the source code
  + Access the simpleHTML repo in github.
  + Edit file index.html
  + Click **Commit changes**.
  ![test](/images/5.test/005.png)

2. Check pipeline in case of "approve"
  + Return to the detail screen of **demo** pipeline.
  + After you commit changes to the repo, CodePipeline will recognize and automatically run the pipeline.
  + You can see, after the **Source** stage runs succeeded, the **Approval** stage will be in **waiting for approval** state.
  ![test](/images/5.test/002.png)
  + At this point, you will receive a notification to Slack.
  ![test](/images/5.test/006.png)
  + If you click **Yes**, the message will change to "Starting to deploy**.
  ![test](/images/5.test/006-1.png)
  + Return to the details screen of the **demo** pipeline, you will see that the pipeline has run to the **deploy** stage.
  ![test](/images/5.test/007.png)
  + After about 3 minutes, the deployment was successful. 
  ![test](/images/5.test/008.png)
  + Access to domain of EB enviroment, you can check whether the deployment process was successful or not.
  ![test](/images/5.test/009.png)
  
3. Check pipeline in case of "reject"
  + Change the source code again
  ![test](/images/5.test/009-1.png)
  + When the slack notification arrives, click **No**. At this time, the screen will show the message "Rejected successfully".
  ![test](/images/5.test/010-1.png)
  + Return to the details screen of the **demo** pipeline, you will see the **Approval** stage change to the **failed** state.
  ![test](/images/5.test/010.png)
  +  Access to domain of EB enviroment, he site still displays the content of the previous commit.
  ![test](/images/5.test/009.png)

  Congratulations, you have just completed the lab. Remember to perform resource cleanup to avoid unintended costs.
