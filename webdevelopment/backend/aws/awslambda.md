# AWS Lambda:
## Introduction:
A compute service that lets you run code without provisioning or managing servers.

## Using the AWS CLI to create a function:
 An example function:
``` exports.handler = async function(event, context) {
  console.log("ENVIRONMENT VARIABLES\n" + JSON.stringify(process.env, null, 2))
  console.log("EVENT\n" + JSON.stringify(event, null, 2))
  return context.logStreamName
} ```
- Create it and zip it ( ``` zip function.zip index.js ``` ).
- Upload it:
``` aws lambda create-function --function-name my-function --zip-file fileb://function.zip --handler index.handler
--runtime nodejs12.x --role arn:aws:iam: **account id** :role/lambda-cli-role ```
- Test it:
``` aws lambda invoke --function-name my-function out --log-type Tail ```
- Retrieve it:
``` aws lambda get-function --function-name my-function ```
- Delete it:
``` aws lambda delete-function --function-name my-function ```

## More about Lambda:
