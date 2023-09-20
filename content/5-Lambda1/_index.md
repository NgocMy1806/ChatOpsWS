---
title : "Create Lambda function to send request approve"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b>5.</b> "
---
1.  Access [AWS Lambda management console](https://us-east-1.console.aws.amazon.com/lambda)
  + Click **Create function**
  ![lambda](/images/lambda/001.png)

2. On **Create function** screen
  + Chọn **Author from scratch**.
  + For **Function name**, enter **sendRequestApprove**.
  + For **Runtime**, select **Python 3.10**.
  + Scroll to the bottom of the page, click **Create function**.
  ![lambda](/images/lambda/002.png)

3. On detail screen of function **sendRequestApprove**

    3.1. Add trigger
  + Click **Add trigger**
  ![lambda](/images/lambda/003.png)
  + Add trigger from service **SNS**.
  + Select topic **demo**.
  + Click **Add**.
  ![lambda](/images/lambda/004.png)

    3.2. Add env
  + Open **Configuration** section.
  + Click **Enviroment variables**
  + Click **Edit**
  ![lambda](/images/lambda/006.png)
  + Add below env:
    + SLACK_CHANNEL
    + SLACK_WEBHOOK_URL
  + Click **Save**  
  ![lambda](/images/lambda/007.png)
  + NOTE: how to get value for key **SLACK_CHANNEL**:
    + Right click on the channel name.
    + Click **Copy**.
    + Click **Copy link**
  ![lambda](/images/lambda/008.png)

    3.3. Write code for function
  + In the **Code** section, delete sample code, then paste the following code.
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
  
