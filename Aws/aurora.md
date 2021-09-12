---
title: Aurora
date: "2020-09-01T03:47:00.000Z"
description: "Aurora"
---

# Aurora
- Not Open sourced
- supports
    - MySql
    - PostgreSql
- cloud optimized database 
    - 5x over mysql
    - 3x over postgress
- storage automatically grows in increment of 10GB upto 64TB
- up to 15 replicas ( 5 in RDS mysql)
- sub 10ms replica lag
- cost 20% more
- Highly available
    - 6 copies of data across 3 AZ
    - self healing if one database is corrupted
- one instance take writes (master)
- automatic fail over in less than 30sec
- supports cross region replication
- reader endpoint and writer endpont
    - during fail over writer endpoint does not change
    - reader endpoints load balanced ( connection level , not statement level )



> **Custom endpoints for subset of read replicas**

## Serverless
- automated database intantiation and auto scalling based on actual usage
- works by proxy fleet


## Multi Master
- if u want immediate failover for write node (HA)
- Every node does read and write - vs promoting a read replica as the master

## Global Aurora
- cross region replicas
- 1 primary region
- up to 5 secondary region , replication lag is less than 1 sec
- up to 16 read replicas per secondary region

## Aurora Machine Learning
- Enable you to add ML- based preditions to your applications by SQL
- supported service 
    - Amazon SageMaker ( ml modal )
    - Amazon Comprehend ( sentiment analysis )
- use cases
    - fraud detection
    - ads targeting
    - product recommendation






