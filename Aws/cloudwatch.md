---
title: CloudWatch 
date: "2020-09-10T16:01:00.000Z"
description: "CloudWatch"
---

# CloudWatch Matrics

- provides metrics for evry service in AWS
- Metric is a variable to monitor
- Metrics belog to namespaces
- Dimension is attribute of a metric
- up to 10 dimensions per metric
- metrics have timestamps
- can create cloudwatch dashboards


## Cloud wathc Custom Metrics
- Possibility to define and send your own custom metrics to cloudWatch
-  eg : memory (RAM) usage, diskspace, number of loggged in users
- have to user API call **PutMetricData**
- Ability to use dimensions ( attributes ) to segment metrics
    - Instance.Id
    - Enviroment.name
- Metric resolution ( StorageResolution Api Parameter - Two possible value )
    - Standard: 1 min
    - High Resolution : 1/5/10/30 - Higher cost

> Accepts metrics data points two weeks in the past and two hours in the future


## Cloudwatch Dashboards
- Dasboards are global
- Dashboards can include grahps from diffrent AWS account and regions
- can cahnge the time zone and tiem range of the dashboards
- pricing
    - 2 dashboards ( up to 50 metrics ) for free
    - $3/dashboard / month afterwards

## Aws CloudWatch Logs
- Applications can send logs to CloudWatch using SDK
- CloudWatch can colect log from 
    - Elastic Beanstalk - collection of logs fromapplication
    - ECS - collection from containers
    - AWS Lambda: Collection from function logs
    - VPC Flow Logs: VPC specific logs
    - API gateway
    - CloudTrail based on filter
    - CloudWatch log agents: for example on EC2 machines
    - Route53: Log DNS queries
- CloudWatch Logs can go to 
    - Batch Exporter to s3 for archival
    - Stream to ElasticSearch cluster for further analysis

### Log storage Architecture
- Log Groups -  arbitary name, usually representing application
- Log stream - inances within application /log files/ containers
- can define log expiration policies ( never expire, 30 days ...)
- Use the Aws CLI we can tail cloudwatch logs
- to send logs to CLoudWatch, make sure IAMp permissions are correct
- logs can be encrypted using KMS at the group level


### CloudWatch Logs Metric Filter And Insights
- CloudWatch logs can use filter expressions
    - find specific IP inside of a log
    - Metric filters can be used to trigger alarms
- CloudWatch logs insight can be sued to query logs and add queries to cloud watch dashboards

### CloudWatch Logs for EC2
- By default, no logs from your EC2 machine will go to CloudWatch
- YOu need to run a cloudwatch agent on EC2 to push the logs files you want
- Make sure IAM permissions are correct
- The CloudWatch log agent can be setup on-premise too
- 2 types of agents
    - CloudWatch log agent
        - old version of the agent
        - can ooly sent to cloudWatch logs
    - Cloud Watch Unified Agent
        - Collects additonal system-level metric such as RAM, processes, etc
        - Collecto logs to sent to CloudWatch Logs
        - Centralized configuration using SSM parameter store

## CloudWatch Alarms
- Alarms are used to trigger notifications for any metric
- Various options ( sampling, %, max, min ... )
- Alarm States
    - OK
    - INSUFFICIENT_DATA
    - ALARM 
- Period 
    - Length of time in seonds to evaluate the metric
    - High resolution custom metrics : 10 sec, 30 sec or multiples of 60 seconds
- Cloud watch targets can be
    - ec2 instance
        - stop, terminate, reboot, or recover an ec2 instance
    - Trigger and autoscalling actions
    - Send notifications to SNS



# CloudWatch Events
- Event Patter : Intercept events from AWS services
    - ec2 instance start, code build failure, s3 , trust advisor
    - can intercept any API call with CloudTrail integration
- Schedule or Cron ( create an event every 4 hours )
- a json payload is createed from the event and passwed to a target
- target can be
    - compute 
        - Lambda, Batch, ECS task
    - Integrations
        - SQS, SNS, Kinesis Data Streams, Kinesis Data Firehose
    - Orchestration
        - Step Functions, CodePipeline, CodeBuild
    - Maintanance
        - SSM,EC2 Actions




