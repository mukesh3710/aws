# Serverless Overview

## What’s serverless?
Serverless is a cloud computing model that allows developers to build and run applications without managing servers. Instead, the cloud provider takes care of the infrastructure, including scaling, patching, and capacity planning.

## Serverless in AWS
AWS offers a comprehensive suite of serverless services, including:
- **AWS Lambda**: Function-as-a-Service (FaaS) for running code.
- **Amazon API Gateway**: For creating and managing APIs.
- **Amazon DynamoDB**: A serverless NoSQL database.
- **AWS Step Functions**: For orchestrating workflows.
- **Amazon S3**: Serverless object storage.

## Why AWS Lambda
AWS Lambda allows you to run code without provisioning or managing servers. It automatically scales applications, supports multiple programming languages, and integrates seamlessly with other AWS services.

## Benefits of AWS Lambda
- **Automatic scaling**: Handles workloads automatically.
- **Cost-effective**: Pay only for the compute time used.
- **Integration**: Works with services like S3, DynamoDB, and API Gateway.
- **Multi-language support**: Includes Python, Node.js, Java, Go, and more.

## AWS Lambda Language Support
- Node.js
- Python
- Java
- Go
- Ruby
- .NET Core
- Custom runtimes

## AWS Lambda Integrations
AWS Lambda integrates with:
- **Event sources**: S3, DynamoDB Streams, SNS, SQS, CloudWatch Events.
- **APIs**: API Gateway for HTTP endpoints.
- **Databases**: RDS, Aurora, and DynamoDB.

## Example: Serverless Thumbnail Creation
1. User uploads an image to S3.
2. S3 triggers a Lambda function.
3. Lambda processes the image and saves the thumbnail to another S3 bucket.

## Example: Serverless CRON Job
1. Use CloudWatch Events to trigger a Lambda function on a schedule.
2. Lambda performs tasks like cleaning logs or sending reports.

## AWS Lambda Pricing: Example
- **Free tier**: 1M requests and 400,000 GB-seconds of compute time per month.
- **Beyond free tier**: $0.20 per 1M requests and $0.00001667 per GB-second.

### Example:
- 1M requests at 512 MB memory for 100 ms: Costs around $0.20.

## AWS Lambda Limits to Know - Per Region
- **Execution timeout**: 15 minutes.
- **Deployment package size**: 50 MB (zip).
- **Memory**: 128 MB to 10 GB.
- **Concurrency**: 1,000 concurrent executions (can be increased).

## Lambda SnapStart
Lambda SnapStart reduces cold start times by initializing functions ahead of time and reusing snapshots for subsequent executions.

## Customization At The Edge
Enhance user experiences by running code closer to users using CloudFront Functions and Lambda@Edge.

### CloudFront Functions & Lambda@Edge Use Cases
- **CloudFront Functions**: Lightweight manipulations like request headers.
- **Lambda@Edge**: Advanced customizations like user authentication or content modification.

### CloudFront Functions
- Built for lightweight, short-duration tasks.
- Ideal for request/response processing.

### Lambda@Edge
- More powerful than CloudFront Functions.
- Can modify content and respond dynamically.

### CloudFront Functions vs. Lambda@Edge
| Feature               | CloudFront Functions   | Lambda@Edge |
|-----------------------|------------------------|-------------|
| Latency              | Low                    | Higher      |
| Runtime              | JavaScript             | Node.js     |
| Use Case             | Header rewrites        | Dynamic content generation |

## Lambda by Default
- Default configurations like retries and timeout values.

## Lambda in VPC
Deploy Lambda functions in a VPC to access RDS, ElastiCache, or other private resources.

## Lambda with RDS Proxy
Improve Lambda database connection efficiency by using RDS Proxy.

## Invoking Lambda from RDS & Aurora
Trigger Lambda functions directly from RDS or Aurora databases using stored procedures.

## RDS Event Notifications
Use Amazon SNS to send notifications about RDS events.

# Amazon DynamoDB

## DynamoDB - Basics
A fully managed NoSQL database designed for fast and flexible performance at scale.

### DynamoDB – Table Example
```json
{
  "TableName": "Users",
  "KeySchema": [
    {"AttributeName": "UserID", "KeyType": "HASH"}
  ],
  "AttributeDefinitions": [
    {"AttributeName": "UserID", "AttributeType": "S"}
  ],
  "ProvisionedThroughput": {
    "ReadCapacityUnits": 5,
    "WriteCapacityUnits": 5
  }
}
```

## DynamoDB – Read/Write Capacity Modes
- **Provisioned**: Specify read/write capacity.
- **On-demand**: Scales automatically.

## DynamoDB Accelerator (DAX)
- In-memory caching for DynamoDB.

### DAX vs. ElastiCache
| Feature      | DAX                 | ElastiCache         |
|--------------|---------------------|---------------------|
| Purpose      | DynamoDB Cache      | General-purpose Cache |

## DynamoDB Streams
Tracks changes in DynamoDB tables for real-time processing.

## DynamoDB Global Tables
Enable multi-region replication for disaster recovery.

## DynamoDB – Time To Live (TTL)
Automatically deletes expired items from a table.

## DynamoDB – Backups for Disaster Recovery
Supports on-demand and continuous backups.

## DynamoDB – Integration with Amazon S3
Export DynamoDB table data to S3 for analytics or backups.

## Example: Building a Serverless API
1. Use API Gateway to accept requests.
2. Use Lambda to process business logic.
3. Store data in DynamoDB.

# AWS API Gateway

## API Gateway – Integrations High Level
Supports Lambda, DynamoDB, and Kinesis as backends.

### Kinesis Data Streams Example
API Gateway invokes Kinesis to ingest real-time data.

## API Gateway - Endpoint Types
- **Edge-optimized**: Best for global users.
- **Regional**: Specific to a region.
- **Private**: Within a VPC.

## API Gateway – Security
- IAM policies
- Lambda authorizers
- Resource policies

# AWS Step Functions
Step Functions help coordinate workflows using Lambda and other services.

# Amazon Cognito

## Cognito User Pools (CUP) – User Features
- User authentication
- Password policies
- Multi-factor authentication

## Cognito User Pools (CUP) - Integrations
Integrates with API Gateway, Lambda, and more.

## Cognito Identity Pools (Federated Identities)
Provide temporary AWS credentials for users.

### Cognito Identity Pools Diagram
Illustrates how identity pools allow federated access to AWS resources.

## Cognito Identity Pools Row-Level Security in DynamoDB
Enforce user-level access controls using IAM policies tied to Cognito identities.

