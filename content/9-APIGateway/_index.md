---
title : "Create API gateway"
date :  "`r Sys.Date()`" 
weight : 9
chapter : false
pre : " <b> 9. </b> "
---
1.  Access [API Gateway management console](https://us-east-1.console.aws.amazon.com/apigateway)
  + Click **Create API**
  ![api](/images/apigateway/001.png)
  + Select type **HTTP API**
  ![api](/images/apigateway/002.png)
2. On **Create an API** screen
  + For **Integrations**, select **Lambda**.
  + For **Lambda function**, select **handleResult**.
  + For **API name**, enter **InteractiveButtonHandler**.
  ![api](/images/apigateway/003.png)

3. On **Configure routes** screen
  + For **Method**, select **POST**.
  + Click **Next**
  ![api](/images/apigateway/004.png)

4. On **Define stages** screen
  + Keep setting default, click **Next**.
 
5. On **Review and create** screen
  + Review information, click **Save**.

6. Get the necessary information
  + Access the details screen of the newly created API, save the **invoke URL** information.
  ![api](/images/apigateway/005.png)
  + Access the **Routes** section, save the routes information of the POST API.
  ![api](/images/apigateway/006.png)