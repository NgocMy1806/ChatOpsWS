---
title : "Introduction"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
In this lab, I will introduce  how to deploy Chatops with AWS service and Slack.

ChatOps is a word created by combining the words Chat and Ops (operation). This is a method of performing tasks related to deploying and operating the system right on chat tools such as Slack, Microsoft Teams, Telegram,...

ChatOps can be used to automate a variety of processes such as:

- Launch applications
- Access data
- Create and update data
- Send emails and notifications
- Create and manage tasks
- Customer support
- Project management
- Track progress
- ...

Within the scope of this lab, I will focus on the practice of sending notifications about the status of the pipeline to the Slack channel, and quickly deploying the application with just 1 click right on Slack

The overall flow is as follows:
  
   You make changes and merge the code into the master branch
→ Pipeline is kicked off

→ At the approval stage, the pipeline will send a notification to AWS SNS, then SNS triggers the Lambda function to send the approval request to the Slack channel

→ the user presses the Approve or Reject button on Slack

→ approval results are sent to CodePipeline via API gateway and Lambda function

→ If approved, CodePipeline will proceed with deployment.

#### AWS CodePipeline
AWS CodePipeline is a fully managed continuous delivery service that helps you automate your release pipelines for fast and reliable application and infrastructure updates.

#### API gateway
Amazon API Gateway is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale. APIs act as the "front door" for applications to access data, business logic, or functionality from your backend services. Using API Gateway, you can create RESTful APIs and WebSocket APIs that enable real-time two-way communication applications. API Gateway supports containerized and serverless workloads, as well as web applications.

#### Amazon SNS
Amazon Simple Notification Service (SNS) is an AWS service used to create, manage, and deliver notifications or messages to various endpoints, including mobile applications, servers, PC and other AWS services.

![Architecture](/images/arc-log.png) 