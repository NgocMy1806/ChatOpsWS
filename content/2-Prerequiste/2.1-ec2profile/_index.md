---
title : "Create Instance Profile"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 2.1.5 </b> "
---

1. Access [Identity and Access Management (IAM) console](https://console.aws.amazon.com/iamv2/home) để tạo instance role
  + Click **Roles**.
  + Click **Create role**.
  
![role](/images/2.prerequisite/ec2profile/001.png)

2. At **Create role** screen
  + For **Trusted entity type**, select **AWS service** 
  + For **Use case**, select **EC2**.

![role](/images/2.prerequisite/ec2profile/002.png)

  + Select policy **AmazonElastiCacheFullAccess**.
![role](/images/2.prerequisite/ec2profile/003.png)  
  + Click **Next**.

  + For **Role name**, enter **WebAppRole**.
  + Scroll to bottom of the page, then click **Create role**.

![role](/images/2.prerequisite/ec2profile/004.png)  
