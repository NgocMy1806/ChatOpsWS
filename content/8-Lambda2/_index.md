---
title : "Create Lambda function to handle approve result"
date :  "`r Sys.Date()`" 
weight : 8
chapter : false
pre : " <b>8.</b> "
---
### Create function
1.  Access [AWS Lambda management console](https://us-east-1.console.aws.amazon.com/lambda)
  + Click **Create function**
  ![lambda](/images/lambda/001.png)

2. On **Create function** screen
  + Chọn **Author from scratch**.
  + For **Function name**, enter **handleResult**.
  + For **Runtime**, select **Python 3.10**.
  + Scroll to the bottom of the page, click **Create function**.
  ![lambda](/images/lambda/009.png)

3. On detail screen of function **handleResult**
  + For **Code**, delete sample code, then paste the following code.
  ```
  # This function is triggered via API Gateway when a user acts on the Slack interactive message sent by approval_requester.py.

from urllib.parse import parse_qs, unquote
import json
import os
import boto3
import base64
import urllib.parse

def lambda_handler(event, context):
    #print("Received event: " + json.dumps(event))
    body_encoded = event['body']
    #decode base64
    body_decoded_base64 = base64.b64decode(body_encoded).decode('utf-8')
    #decode url
    body = urllib.parse.unquote(body_decoded_base64)
    #remove "payload"
    body = body[len('payload='):]
    payload = json.loads(body)
    print(payload)
    print(type(payload))        

    action_details = payload['actions'][0]['value']
    # remove + in action_details
    action_details=action_details.replace('+', '')
    action_details = json.loads(action_details)
    
    codepipeline_status = "Approved" if action_details["approve"] else "Rejected"
    codepipeline_name = action_details["codePipelineName"]
    token = action_details["codePipelineToken"] 
    
    if codepipeline_status == "Approved":
      message = "Starting to deploy"
    else:
      message = "Rejected successfully"
    
    client = boto3.client('codepipeline')
    response_approval = client.put_approval_result(
                            pipelineName=codepipeline_name,
                            stageName='Approval',
                            actionName='ApprovalOrDeny',
                            result={'summary':'','status':codepipeline_status},
                            token=token)
    print(response_approval)
    return {
            "statusCode": 200,
            "body": meassage
        }

  ```
  

  + Click **Deploy**.
![lambda](/images/lambda/010.png)
  
### Add permission for lambda function.
  Because this function needs to call the API to CodePipeline to send approval results, we will need to add the permission **codepipeline:PutApprovalResult** to the function.
1. Access [IAM management console](https://us-east-1.console.aws.amazon.com/iamv2)
  + Open menu **Roles**, find the role of the Lambda function **handleResult**.
  + Click on the role name to open the details screen.
    ![lambda](/images/lambda/011.png)
2. On detail screen of **handleResult** role.
  + Click **Add permission**, select **Attach policies**.
    ![lambda](/images/lambda/012.png)
  + Tick on permission **AWSCodePipelineApproverAccess**.
  + Click **Add permission**.
    ![lambda](/images/lambda/013.png)