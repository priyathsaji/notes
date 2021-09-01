---
title: ASG
date: "2020-09-01T03:47:00.000Z"
description: "Auto Scalling Groups"
---

# Auto Scalling Groups
- scalling application based on the real time load
- can be with or without load balencer
- **scale out** - increasing instances to match the load
- **scale in** - decreasing instances to match decreased load
- ensure **minimum number and maximum of instances is running**
- automatically register new instances to load balencer
- IAM rule attached to ASG will be assigned to EC2
- requirements
    - AMI + Instance Type 
    - Ec2 User Data
    - EBS Volumns
    - Security Groups
    - Key Pair
    - minimum and maximum capacity
    - load balencer information
    - scalling policy
- scalling is based on **CloudWatch Alarms**
- scalling rules can be based on 
    - average cpu usage
    - number of requests
    - average network in
    - average network out
    - schedule ( specific time )
    - custom matric (eg: number of connected users)
        - send custom matric to cloud watch alarm **PutMetric API**
        - create cloud watch alarm to react to low/ high values
        - use cloud watch alarm as the scalling policy for ASG


# Scaling Policies
- Dynamic Scalling
    - Target Tracking Scalling
        - eg: average cpu to stay around 40%
        - creates a cloud watch alarm for us
        - common metrics like cpu, network request based cloud watch alarm can be created automatically
    - Simple scaling
        - cloud watch alarm triggered
    - step scalling
        - multiple cloud watch alarms
        - based on alarms scale out and scale in
- Scheduled Actions
    - anticipated usage pattern
- Predictive scalling
    - forcast based scalling
    - machine learning powered

> Cool down period: after a scalling activity u will be in cool down period. (default 300 seconds) scaling wont happen during this time

# Termination Policy
- default 
    - find AZ with most number of instances
    - delete one with oldest configuration
    - **tries to balence the number of instances across AZ**
# Lifecycle hooks
- ablity to perform extra steps before instance goes into service and instance goes out or service
- scale out
    - pending wait
    - pending proceed
- scale  in 
    - terminating wait
    - terminating proceed 




