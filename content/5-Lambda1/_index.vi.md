---
title : "Tạo Lambda function gửi request approve"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b>5.</b> "
---
1.  Truy cập vào [giao diện quản trị của dịch vụ AWS Lambda](https://us-east-1.console.aws.amazon.com/lambda)
  + Click **Create function**
  ![lambda](/images/lambda/001.png)

2. Tại màn hình **Create function**
  + Chọn **Author from scratch**.
  + Tại mục **Function name**, nhập **sendRequestApprove**.
  + Tại mục **Runtime**, chọn **Python 3.10**.
  + Scroll xuống cuối trang, click **Create function**.
  ![lambda](/images/lambda/002.png)

3. Tại màn hình detail của function **sendRequestApprove**

    3.1. Thêm trigger
  + Click **Add trigger**
  ![lambda](/images/lambda/003.png)
  + Chọn trigger từ service **SNS**.
  + Chọn topic **demo** vừa tạo.
  + Click **Add**.
  ![lambda](/images/lambda/004.png)

    3.2. Thêm env
  + Mở mục **Configuration**.
  + Click **Enviroment variables**
  + Click **Edit**
  ![lambda](/images/lambda/006.png)
  + Thêm các env sau:
    + SLACK_CHANNEL
    + SLACK_WEBHOOK_URL
  + Click **Save**  
  ![lambda](/images/lambda/007.png)
  + NOTE: cách lấy value cho key **SLACK_CHANNEL**:
    + Click chuột phải vào tên channel.
    + Click **Copy**.
    + Click **Copy link**
  ![lambda](/images/lambda/008.png)

    3.3. Viết code cho function
  + Tại mục **Code**, xóa hết phần code sample có sẵn, rồi paste đoạn code sau vào.
  ```
  # This function is invoked via SNS when the CodePipeline manual approval action starts.
# It will take the details from this approval notification and sent an interactive message to Slack that allows users to approve or cancel the deployment.

import os
import json
import logging
import urllib.parse

from base64 import b64decode
from urllib.request import Request, urlopen
from urllib.error import URLError, HTTPError

SLACK_WEBHOOK_URL = os.environ['SLACK_WEBHOOK_URL']
SLACK_CHANNEL = os.environ['SLACK_CHANNEL']

logger = logging.getLogger()
logger.setLevel(logging.INFO)

def lambda_handler(event, context):
    print("Received event: " + json.dumps(event, indent=2))
    message = event["Records"][0]["Sns"]["Message"]
    
    data = json.loads(message) 
    token = data["approval"]["token"]
    codepipeline_name = data["approval"]["pipelineName"]
    
    slack_message = {
        "channel": SLACK_CHANNEL,
        "text": "Would you like to promote the build to production?",
        "attachments": [
            {
                "text": "Yes to deploy your build to production",
                "fallback": "You are unable to promote a build",
                "callback_id": "wopr_game",
                "color": "#3AA3E3",
                "attachment_type": "default",
                "actions": [
                    {
                        "name": "deployment",
                        "text": "Yes",
                        "style": "danger",
                        "type": "button",
                        "value": json.dumps({"approve": True, "codePipelineToken": token, "codePipelineName": codepipeline_name}),
                        "confirm": {
                            "title": "Are you sure?",
                            "text": "This will deploy the build to production",
                            "ok_text": "Yes",
                            "dismiss_text": "No"
                        }
                    },
                    {
                        "name": "deployment",
                        "text": "No",
                        "type": "button",
                        "value": json.dumps({"approve": False, "codePipelineToken": token, "codePipelineName": codepipeline_name})
                    }  
                ]
            }
        ]
    }

    req = Request(SLACK_WEBHOOK_URL, json.dumps(slack_message).encode('utf-8'))

    response = urlopen(req)
    response.read()
    
    return None

  ```
  

  + Click **Deploy**.
![lambda](/images/lambda/005.png)
  
