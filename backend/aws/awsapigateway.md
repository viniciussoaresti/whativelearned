# AWS Api-Gateway
## Introduction:
It's an AWS service for creating, publishing, maintaining, monitoring, and securing REST and WebSocket APIs at any scale.
It can map the client's request to a 'event' parameter, that Lambda functions comsume.
## Creating an API:
- 1: Create a Lambda Function (https://console.aws.amazon.com/lambda/home);
- 2: Create a REST API in the console (https://us-east-2.console.aws.amazon.com/apigateway/home?region=us-east-2);
- 3: Create methods:
e.g.: ``` get method -> integration type lambda function -> lambda proxy integration ```
- 4: Deploy API:
e.g. ``` actions -> deploy API -> deployment stage prod -> deploy  ```
- 5: To add a parameter to pass (and a template):
See this [link](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-getting-started-with-rest-apis.html), from sections 13 to 23.