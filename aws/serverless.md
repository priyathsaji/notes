---
title: Serverless
date: "2020-09-06T18:47:00.000Z"
description: "Serverless"
---

# Serverless
- new paradigm in which developers don't have to manange servers anymore
- just deploy code 
- services
    - AWS Lambda
    - DynamoDb
    - AWS Cognito
    - AWS API gateway
    - AWS s3
    - SNS and SQS
    - Kinesis Data firehouse
    - Aurora Serverless
    - Step Functions
    - Fargate

# Lambda
- Vitual functions -no servers to manage
- Limited by time - short executions ( 15 mins )
- Run on-Demand
- scaling is automated
- up to 10 gb of ram per functions
- Lambda Container Image
    - The containter image implemented the Lambda RunTime API
    - for custom languages not supported directly by lambda
- to Schedule lambda functions u need to use ( chron job )
    - configure a cloudwatch event based on schedure
    - invoke lambda
- Execution
    - 128MB to 10GB ram ( 64 GB increments )
    - Maxium execution time : 900 sec ( 15 mins )
    - Enviroment Variables 4 KB
    - Disk Capacity : 512 MB
    - concurrent Execution 1000 ( can be increased )
- Deployment
    - deployment size 50 MB
    - uncompressed deployement code size : 250 MB
    - can use /temp director to load other files at startup
    - Enviroment Variables 4 KB

## Lambda Edge
- if u want to run Lambda alongside the cnd using cloudfront
- you can use lambda to chagne cloud front request and resonse
    - after cloudfront receives a reqest from a viewer can be modified ( **viewer request** )
    - before cloudfront forwards the request to the origin ( **orgin request**)
    - after cloudfront receives the response from the origin ( **origin response**)
    - generate responxes to the viewers without ever sending the request to origin ( **viewer response** )

 # Dynamo DB
 - fully managed, Highly available with replication across 3 AZ
 - NoSql database
 - scales to massive works loads
 - enales event driven programming with DynamoDb Streams
 - has
    - tables
    - primary keys
    - infinite number of items ( rows )
    - item has attributes (max size 400KB)
- Provisioned Throughput
    - table must have provisioned readn and write capacity units
    - **Read Capacity Units (RCU)**: throughput for reads 
        - 1 RCU = 1 strongly consistant read for 4 KB per second
        - 1 RCU = 2 eventually consistant read of 4 KB per second
    - **Write Capcity Units (WCU)**: throughput for writes
         - 1 WCU - 1 write of 1KB per second
    - throughtput can be execued temporarily using 'burst credit'
- **DAX - DynamoDB Accelerator**
    - seamless cache for DynamoDB
    - writes go through DAX to DynamoDB
    - Microsecond latency for cached reads and queries
    - 5 mins TTL for cache entry
- DynamoDB Streams
    - changes the DynamoDb ( create, Update, Delete ) can end up in Streams
    - this can be read by lambda
        - to react to real time 
        - analytics
        - insert to elastic search
    - 24 hours of data retention
- Transactions
- On Demand ( scales automatically )
- Global Tables
    - multi region, full replicated , high performance
    - must enable DynamoDB Streams


# API Gateway
- rest api services to trigger to access aws services
- swagger/ open api import support
- cache API response
- websockets supported
- Endpoint types
    - Edge-Optimized ( default )
    - Regional 
    - Private
        - can only accessed within your VPC
- Security
    - can use IAM policy for users who has AWS account
        - uses "Sig v4" capability when IAM credential are i headers
    - lambda Authorizer
        - valid token in header by lambda
        - should return IAM policy of the user
    - Congito User Pool  ( authentication, not autorization )

# AWS Cognito
- **Cognito User Pools**
    - Sign in functionality for app users
    - integrate with API gateway
    - serverless database for users
    - can enable federated identies ( Facebook, google )
    - sends back JWT
    - can be integrated with API gateway for Authentication
- **Cognito Identity Pools**  Federated Identity
    - Provide AWS credentials to users so that they can access AWS resource directly
    - Integrate with Cognito User Pools as as identity provider
    - process 
        - get auth token from authentication provider ( google , facebook )
        - sent auth token in headers to congito identy pool
        - cognito verfies the token by connecting to authentication provider
        - generates temporary credentials by STS 
        - return the token to app
        - this token can be used to access aws services
- **Cognito Sync**
    - synchronize data from device to Cognito
    - replaced by AppSync
    - store preferences, configuration, state of app
    - requires Federated Identity Pool
    - store data in datasets
    - upto 20 datasets

# SAM - Serverless Application Modal 
- framework used for developing and deploying serverless applications
- all configuration is YAML code
- can help u run lambda, API gateway ,DynamoDb Locally
- can use CodeDeploy to deploy lambda functions








