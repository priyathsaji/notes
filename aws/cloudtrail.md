---
title: Event Bridge 
date: "2020-09-10T16:01:00.000Z"
description: "Event Bridge"
---

# Cloud Trail
- Provides governance, compliance and audit for your aws account
- Cloud trail is enabled by default
- Get an history of events/ API calls made within your AWS account
    - console
    - SDK
    - CLI
    - Aws services
- Can put logs from Cloud Trail into CloudWatch logs or s3
- A trail can be applied to All regions ( default ) or a single region
- if a resource is deleted in AWS, investigate CloudTrail first
- events are kept for 90 days in cloudTrail
- to keep events beyond this period, log them in s2 and use athena


## Types of events
- Management events
    - Operations that are performed on resources in oyou aws account
    - configuring security ( IAM AttachRolePolicy )
    - configuring rules for routing data 
    - setting up logging
    - can separate **Read Events** ( that dont modify the resources ) **Write Events** ( that modify resources)
- Data Events
    - By default not logged
    - S3 object-level activity ( can separate Read and write events )
        - getObject
        - DeleteObject
        - PutObjects
    - Lambda function execution activity ( the invoke API )
- CloudTrail Insight Events
    - Enable Cloud Insights to detect unusual activity in your account
        - inaccurate resource provisioning
        - hitting service limit
        - bursts of AWS IAM actions
        - Gaps in peridic maintenance activity
    - Cloudtrail analyses normal manangement events to create a baseline
    - conituously analyzes write events to detect unusual patterns
        - anomalies appear in CloudTrail console
        - Event is sent to Amazon s3
        - An EventBridge event is generated ( for automation needs )