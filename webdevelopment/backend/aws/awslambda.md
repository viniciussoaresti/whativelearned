# AWS Lambda:
## Introduction:
A compute service that lets you run code without provisioning or managing servers.

## Using the AWS CLI to create a function:
- An example function:
``` exports.handler = async function(event, context) {
  console.log("ENVIRONMENT VARIABLES\n" + JSON.stringify(process.env, null, 2))
  console.log("EVENT\n" + JSON.stringify(event, null, 2))
  return context.logStreamName
} 
```
- Create it and zip it ( ``` zip function.zip index.js ``` ).
- Upload it:
```
 aws lambda create-function --function-name my-function --zip-file fileb://function.zip --handler index.handler
--runtime nodejs12.x --role arn:aws:iam: **account id** :role/lambda-cli-role 
```
- Test it:
``` aws lambda invoke --function-name my-function out --log-type Tail ```
- Retrieve it:
``` aws lambda get-function --function-name my-function ```
- Delete it:
``` aws lambda delete-function --function-name my-function ```
## Event Source Mapping
Lambda runs on event triggers. DynamoDB can have Streams, that update every time that something is added or deleted. Get where I'm going?
 ```
 $ aws lambda create-event-source-mapping --function-name my-function --batch-size 500 --starting-position LATEST \
--event-source-arn arn:aws:dynamodb:us-east-2:123456789012:table/my-table/stream/2019-06-10T19:26:16.525
{
    "UUID": "14e0db71-5d35-4eb5-b481-8945cf9d10c2",
    "BatchSize": 500,
    "MaximumBatchingWindowInSeconds": 0,
    "ParallelizationFactor": 1,
    "EventSourceArn": "arn:aws:dynamodb:us-east-2:123456789012:table/my-table/stream/2019-06-10T19:26:16.525",
    "FunctionArn": "arn:aws:lambda:us-east-2:123456789012:function:my-function",
    "LastModified": 1560209851.963,
    "LastProcessingResult": "No records processed",
    "State": "Creating",
    "StateTransitionReason": "User action",
    "DestinationConfig": {},
    "MaximumRecordAgeInSeconds": 604800,
    "BisectBatchOnFunctionError": false,
    "MaximumRetryAttempts": 10000
}
```
## More about Lambda:
On docs.