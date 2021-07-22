# AWS DAX:
## Introduction:
It’s a cache in memory for DynamoDB. It offers up to 10 times better performance and it’s
compatible with DynamoDB API calls. DAX is better when you use a lot of read operations
in the same endpoints, if you use a single a read operation, maybe DAX is not needed.
## How to implement:
If you need to define a DAX accelerator, first you have to change your sam template to use a
VPC, with SecurityGroupIds,SubnetIds, Security Group,VPC,
SecurityGroupIngress.