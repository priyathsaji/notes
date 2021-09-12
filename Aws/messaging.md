---
title: Messaging
date: "2020-09-01T03:47:00.000Z"
description: "Messaging"
---

# SQS - Simple Queue Service

- Producer - prodeuces messsages
- Consumers - Poll Messages to take messages from queue
    - recieve an process the messages in parallel
    - atleast one delivery

- Standard Queue
    - Fully Managed Service
    - Unlimited throughtput and unlimited number of messages
    - default retention 4 days, maximum 14 days
    - low latency
    - max size 256 KB
    - can have duplicate messages
    - can have out of order messages (**best efford ordering**)
    
- Encryption 
    - in flight encryption - HTTPS API
    - At rest encryption KMS key
- Access  Controll
    - IAM Policies to regulate access to the SQS API
    - SQS Access Policies ( similar to s2 bucket policies )


## SQS - queue access policy

- Cross Account Access
    ```json
    {
        "version":"2012-10-07",
        "Statement":[{
            "Effect":"Allow",
            "Principal":{"AWS":["112222333323"]}, // account id of of the target account user
            "Action":["sqs:ReceiveMessage"],
            "Resource":"arn:aws:sqs:us-east-1:444333222:queue1" /// account id of of the source account user
        }]

    }
    ```
- Public s3 event Notifications to SQS Queue
    ```json
    {
        "version":"2012-10-07",
        "Statement":[{
            "Effect":"Allow",
            "Principal":{"AWS":"*"]}, 
            "Action":["sqs:SendMessage"],
            "Resource":"arn:aws:sqs:us-east-1:444333222:queue1",
            "Condition":{
                "ArnLike":{"aws:SourceArn":"arn:aws:s3:*:*:bucket1"},
                "StringEquals":{"aws:SourceAccount":"<<bucket_owner_account_id"}
            }
        }]

    }
    ```

## Message Visibility Timeout
- Once after a message is polled by a consumer. that message will be invissible to other consumers.. Until Visibilty timeout.. or in case the message is deleted
- by default the visibility timeout is 30 sec
    - once message is polled by the consumer, it has 30 seconds to process that message. if not done it will be returned again to the queue. so that it will be visible to other consumers to poll
    - if the consumer required more time to process api, it can use **ChangeMessageVisibility** Api to get more time

## Dead Letter Queue
- if the consumer fails to process a message within the Visibilty Timeout. the message goes back to the queue
- we can set a threshold of how many times a message can go back to the queue
- if that threshold (**MaximumReceives** )is reached.. it can be moved to another queue called
**Dead letter queue** so it can be analysed separatly

## SQS - Request-Response Systems
- **SQS Temporary queue Client** can be used to implement request response pattern using SQS 
- Temporary queue Client is a virtual queue.( creating /deleting is cost effective )

## Delay Queue
- Delay a message upto 15 mins ( consumer dont see it immediately )
- default 0 seconds
- can set value at queue level
- can override default value during sent by **DelaySeconds** parameter

## FIFO Queue
- messages will be ordered in queue
- limited throughput of 300 msg/s without batching, 3000 msg/s with batching
- queue name  should end with **.fifo**


# SNS - Simple Notification Service
- sent one message to many receivers
- pub / sub pattern
- event producer sent messages to one topic
- can have any number of event receivers for that topic
- suscribers can be 
    - SQS
    - HTTP / HTTPS
    - Lambda
    - Email Notifications
    - Mobile Notifications 
- Encryption
    - in flight encryption using HTTPS
    - at rest using KMS keys
    - client side encryption if needed by client
- Access Control
    - IAM Policies
    - SNS Acces Policies
        - can be usefull for allowing other service to write to an SNS topic
        - can be usefull for cross-account access to SNS topic
- SNS also support FIFO
- JSON policy can be used to filter messages sent to SNS topic's subscribers
    - if not filter policy every message will be sent to subscriber

# Kinesis
- easy to collect process ans analyze streaming data in real-time
- ingest real-time data such as : Application logs, metrics, iot telemetry data...
- **Kinesis Data Streams** : capture , process and store data streams
    - consists of shards
    - can scale number of shards
    - producers can producer a **Record** to Kinesis Data Stream
    - Record contains
        - data
        - partition key 
    - the record from Kinesis data Stream can be sent to 
        - Lambda
        - Custom Applicaitons
        - Kinesis Firehose
        - Kinesis Data analytics
    - Record sent from data streams consists of an extra **Sequence No** due to shards
    - data retention 1 to 365 days
    - ablity to reprocess / replay data
    - once data is inserted it cannot be deleted
    - data with same partion key goes to same shard

- **Kinesis Data Firehose** : load data into AWS data stores- 
    - can read from
        - cloud watch
        - aws iot
        - kinesis data streams
        - custom applications
    - can transform the data using lambda functions
    - can batch write to databases
        - s3
        - Redshift
        - Elastic Search
        - custom HTTP endpint
        - 3rd party destination :eg : mongo db
    - all or failed data can be sent to an s3 bucket
    - near real time
    - fully managed service

- **Kinesis Data Analytics** : analyze data streams with SQL or Apache Flink
    - if you want to write sql on streaming data
    - source can be 
        - kinesis data streams
        - kinesis firehose
    - target can be 
        - kinesis data streams
        - kinesis firehose
    - peform real time analytics on kinesis stream using sql 
- **Kinesis Video Streams**: capture, process and store video streams


# Amazon MQ
- if the appplication uses a open source protocol for messaging and has to be migrated to cloud
- some of open source messaging protocols include
    - MQTT
    - AMQP
    - STOMP
    - OpenWire
    - WSS
- runs on a dedicated machine, can run in HA with failover
- has both queue feature and topic feature






