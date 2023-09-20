---
title : "Create pipeline"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b>2.3</b> "
---

1.  Access [CodePipeline management console](https://us-east-1.console.aws.amazon.com/codesuite/codepipeline/pipelines).
  + Click **Create Pipeline**.
  ![pipeline](/images/pipeline/000.png)

2. On **Choose pipeline settings** screen
  + For **Pipeline name**, enter **demo**.
  + Click **Next**.
  ![pipeline](/images/pipeline/001.png)

3. On **Add source stage** screen
  + For **Source provider**, select **GitHub (version 2)**.
  + For **Connection**, click **Connect to GitHub**.
  ![pipeline](/images/pipeline/002.png)

  + For **Connection name**, enter **demo**.
  + Click button **Connect to Github**.
  ![pipeline](/images/pipeline/003.png)
  + Click button **Install a new app**.
  + Login to github.
  + On **Install AWS Connector for GitHub page** screen, click **Select repositories** and select repo **simpleHTML**.
  ![pipeline](/images/pipeline/004.png)
  + Click button **Save**.
  + After that, you will be redirected to the **Connect to Github** screen.
  + Click the **Connect** button to complete the connection to Github.
  ![pipeline](/images/pipeline/005.png)
  + After that, you will be redirected to the **Add source stage** screen.
  + At this time, the connection status has changed to **ready**.
  + For **Repository name**, select repo **simpleHTML**.
  + For **Branch name**, select **main**.
  + Click button **Next**.
  ![pipeline](/images/pipeline/006.png)

4. On **Add build stage** screen
  + Click **Skip build stage**.
  ![pipeline](/images/pipeline/008.png)

5. On **Add deploy stage** screen
  + For **Deploy provider**, select **AWS Elastic Beanstalk**.
  + For **Application name**, select **demo**.
  + For **Environment name**, select **demo**.
  + Click **Next**.
  ![pipeline](/images/pipeline/009.png)

6. On **Review** screen
  + Review information
  + Scroll to the bottom of the page, click **Create pipeline**.