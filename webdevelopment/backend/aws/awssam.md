# AWS SAM:
## Introduction:
AWS SAM is composed of two things: Template and CLI.

## Template:
Describes the functions, APIs, permissions, configurations, and events that make up a serverless application.
It's only a file, named 'template.yml' (can you believe it?).
It has a couple of arguments, in which only Transform and Resources are required, the others
are optional:
### Template tags:
-Transform: Put 'Transform: AWS::Serverless-2016-10-31' on the file. Just accept it.
-Globals: It contains information and configuration that is shared on the Function, API and SimpleTable tags.
-Resources: The actual functions, APIs ,(...), that make up the app.
-Description: Could you guess what this is?
-Metadata: Could you guess what this is?
-Parameters: Values that you can refer to on Resources and Outputs.
-Mappings: Like a lookup table.
-Conditions: Specify if some resources are used or not depending on some factors (e.g.: test environment).
-Outputs: Describes values.

Example of template:
'Globals:
  Function:
    Runtime: nodejs6.10
    Timeout: 180
    Handler: index.handler
    Environment:
      Variables:
        TABLE_NAME: data-table

Resources:
  HelloWorldFunction:
    Type: AWS::Serverless::Function
    Properties:
      Environment:
        Variables:
          MESSAGE: "Hello From SAM"

  ThumbnailFunction:
    Type: AWS::Serverless::Function
    Properties:
      Events:
        Thumbnail:
          Type: Api
          Properties:
            Path: /thumbnail
            Method: POST'

