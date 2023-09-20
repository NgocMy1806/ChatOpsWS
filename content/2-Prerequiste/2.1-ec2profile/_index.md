---
title : "Create instance profile"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 2.1</b> "
---

1. Access [IAM management console](https://console.aws.amazon.com/iamv2/home) to create instance role
  + Click **Roles**.
  + Click **Create role**.
  
![role](/images/2.prerequisite/ec2profile/001.png)

2. On **Create role** screen
  + For **Trusted entity type**, select **AWS service** 
  + For **Use case**, select **EC2**.

![role](/images/2.prerequisite/ec2profile/002.png)


  + Select policy **AWSElasticBeanstalkWebTier**.
![role](/images/2.prerequisite/ec2profile/003-1.png)  
  + Click **Next**.

  + For **Role name**, enter **WebAppRole**.
  + Scroll to the bottom of the page, click **Create role**.

![role](/images/2.prerequisite/ec2profile/004.png)  

