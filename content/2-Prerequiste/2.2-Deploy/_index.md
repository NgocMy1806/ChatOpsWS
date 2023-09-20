---
title : "Deploy application"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b>2.2</b> "
---
#### Prepare application
+ Please create a **simpleHTML** repo on your github account, in that repo just create a simple index.html file as follows.
```
<html>
  <body>
    <h1>Welcome to the demo-pipeline website</h1>
    <p>This is the index page</p>
  </body>
</html>
```
  ![EB](/images/2.prerequisite/eb/001-0.png)

#### Deploy application
1.  Access [Amazon Elastic Beanstalk management console](https://console.aws.amazon.com/elasticbeanstalk/home).
  + Click **Create application**.
  ![EB](/images/2.prerequisite/eb/001.png)
    
2. On **Configure environment** screen
  + For **Environment tier**, select **Web server environment**.
  + For **Application name**, enter **demo**.
  + For **Domain**, enter the domain you want and press **Check availability** to see if you can use that domain.
  ![EB](/images/2.prerequisite/eb/002.png)

  + For **Platform**, select **PHP**.
  + For **Application code**, select **Sample application**.
  + Scroll to the bottom of the page, click **Next**.
  ![EB](/images/2.prerequisite/eb/003.png)

3. On **Configure service access** screen
  + For **Service role**, select **aws-elasticbeanstalk-service-role**.
  + For **EC2 instance profile**, select **WebAppRole**.
  + Click **Next**
  ![EB](/images/2.prerequisite/eb/004.png)

4. On **Set up networking, database, and tags** screen
  + For **VPC**, select **default-vpc**.
  + For **Public IP address**, tick on checkbox **Activated**.
  + For **Instance subnets**, select 1 public subnet.
  + Scroll to the bottom of the page, click **Next**
  ![EB](/images/2.prerequisite/eb/005.png)

5. On **Configure instance traffic and scaling** screen
  + For **EC2 security groups**, select **default**.
  ![EB](/images/2.prerequisite/eb/006.png)
  + Scroll down, for **Instance types**, select **t2.micro**.
  ![EB](/images/2.prerequisite/eb/008.png)
  + Scroll to the bottom of the page, click **Next**.

6. On **Configure updates, monitoring, and logging** screen
  + Scroll to the bottom of the page, click **Next**.

7. On **Review** screen
  + Scroll to the bottom of the page, click **Submit**.

 
