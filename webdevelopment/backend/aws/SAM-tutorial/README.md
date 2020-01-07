# Packaging:
``` sam package --template-file template.yml --output-template-file package.yml --s3-bucket buckettestvsti ```

# Deployment:
``` sam deploy --template-file package.yml --stack-name teststackrenew --capabilities CAPABILITY_IAM --region us-east-2 ```