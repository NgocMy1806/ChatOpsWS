---
title : "Chatops"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
---
# Chatops with AWS service and Slack

### Overall

 In this lab, I will introduce  how to deploy Chatops with AWS service and Slack.
 This is a simple lab to help you understand what chatops is, how to deploy chatops at a basic level. After completing it, you can apply it to real projects with more complex configurations (eg specifying users who have the right to press the Approve button on Slack, add stage build code, configure AWS chatbot so you can type commands directly on Slack, etc.)
 
 We hope this lab will help you in your "Cloud journey"!

![Architecture](/images/arc-log.png) 

### Content

 1. [Introduce](1-introduce/)
 2. [Prerequiste](2-prerequiste/)
 3. [Config Slack app](3-configslackapp/)
 4. [Create SNS topic](4-createsnstopic/)
 5. [Create Lambda function 1](5-lambda1/)
 6. [Add stage Approval](6-approvalstage/)
 7. [Test send noti](7-testsendrequest/)
 8. [Create Lambda function 2](8-lambda2/)
 9. [Create API Gateway](9-apigateway)
 10. [Enable SlackInteractivity](10-slackinteractivity)
 11. [Test](11-test/)
 12. [Clean up resources](12-cleanup/)
