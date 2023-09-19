---
title : "Create Lambda function to handle approve result"
date :  "`r Sys.Date()`" 
weight : 8
chapter : false
pre : " <b>8.</b> "
---
### Tạo function
1.  Truy cập vào [giao diện quản trị của dịch vụ AWS Lambda](https://us-east-1.console.aws.amazon.com/lambda)
  + Click **Create function**
  ![lambda](/images/lambda/001.png)

2. Tại màn hình **Create function**
  + Chọn **Author from scratch**.
  + Tại mục **Function name**, nhập **handleResult**.
  + Tại mục **Runtime**, chọn **Python 3.10**.
  + Scroll xuống cuối trang, click **Create function**.
  ![lambda](/images/lambda/009.png)

3. Tại màn hình detail của function **handleResult**
  + Tại mục **Code**, xóa hết phần code sample có sẵn, rồi paste đoạn code sau vào.
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
  
### Thêm permission cho lambda function.
  Vì function này cần gọi API đến CodePipeline để gửi kết quả approve, cho nên chúng ta sẽ cần thêm permission **codepipeline:PutApprovalResult** cho function.
1. Truy cập vào [giao diện quản trị của dịch vụ IAM](https://us-east-1.console.aws.amazon.com/iamv2)
  + Mở menu **Roles**, tìm role của function Lambda **handleResult**.
  + Click vào role name để mở màn hình details
    ![lambda](/images/lambda/011.png)
2. Tại màn hình detail của role **handleResult**.
  + Click **Add permission**, chọn **Attach policies**.
    ![lambda](/images/lambda/012.png)
  + Tick vào permission **AWSCodePipelineApproverAccess**.
  + Click **Add permission**.
    ![lambda](/images/lambda/013.png)