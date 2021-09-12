---
title: Databases
date: "2020-09-06T18:47:00.000Z"
description: "Databases"
---

# RDS
- managed PostgreSQL/ MYSQL / Oracle / SQL Server
- must provision ec2 instane and es volumn type ans size
- support for read replicas and Multi AZ
- support for IAM, security groups, KMS, SSL in transit
- Backup/ snapshot / Point in time restore feature
- Monotoring through cloudwatch

> storate relational datasets , perform SQL queries, transactional inserts, update , delete available

- very small down time
- pay per hour based on provisioned ec2 and ebs

# Aurora
- Compatible with PostGreSql and Mysql,
- data held in 6 replicase, across 3 AZ
- auto Healing capablity
- read replicas can be global
- auto scaling of storage from 10gb to 64 TB
- define ec2 instance type for aurora instances
- aurora serverless - for unpredictable worklods
- auroa multi- master - for continuous write failover

> same as RDS, but witl less maintanance/ more flexiblity / more performance ( cloud optimized version )


# Elastic Cache
- Managed Redis/ Memcached
- In memory
- must provision ec2 instance
- support for clustering ( Redis ) and multi AZ, read replicas ( sharding )
- backup / snapshot / point in time restore feature

> keyvalue store mainly used for caching, frequent reads, less writes, cache result for db, queries, store session data for websites, cannot use SQL

# Dynamo DB
- AWS proprietary technology, managed NoSql database
- serverless, autoscallin
- can be replacement for elasticcache
- highly available, can provision read and write units independently, **DAX** for read cache
- reads can be eventually consistant and strongly consistant
- security done through IAM
- Dynamo db streams to integrate with AWS lambda
- **can only query on primary key , sort key or indices**

> severless application development ( small documents 100s KB ), distributed serverless cache


# S3 
- S3 is a key valuye store for objects
- great for4 big objects, not so great for small objects
- serverless, scales infinitel, max object size 5 TB
- strong const6ancey
- differnent tiers
- versioning, encryptiohn, cross region replication
- security IAM, bucket policy, ACL

> static files, key value store,for big files,web hosting

# Athena

- Fully serverless
- user to query data in s3
- pay per query
- output back to s3
- secured throught IAM

> one time Sql queries, serverless queries on s3, log analytics


# Reshift
- based on PostGreSQL, used for OLAP
- can scale to PS of data
- columnar storage of data 
- massively parallel query executionm
- pay as you go
- integration with BI tools such as AWS quicksite or Tableau 
- data can be loaded fro s3 DynamoDB,DMS
- can have 1 to 128 nodes, upt to 160 GB of space per node
- Leader node, for query planning, result aggregation
- Compute node, for performing the queries, sent the result to leader
- Redshift Spectrum, perform queries directly against s3 ( no need to load )
- Reshift Enahanced VPC Routing, COPY/ UNLOAD goes through VPC
- **no multi-AZ mode**
- snapshots are point in time backups of a cluster, stored internally in s3
- snapshots are incremental
- can restore snapshot toa new cluster
- automated every 8 hours, evey 5 GB or on a schedule, set rentino
- manual,snapshots is retained until you delete it
- can configure to copy snapshot to another AWS Region
- injesting data to red shit
    - kinesis firehouse
    - s3 copy command
        - thought public internet
        - through enhanced vpc routing
    - ec2 instance jdbc driver
- 
## Read shift spectum 

- query data that is already in s3 without loading it
- must have a redshift cluster available to start the query
- query is then submitted to thousands of redshift spectrum nodes

# Glue
- managed ETL Service
- used to perpare transform data for analytics
- fully serverless service

## Glue data catalog
- metadata of data present in 
    - s3
    - rds
    - dynamo db
    - jdbc
- has Glue data crawler
    - to get metadata from various sources
    - write data to glue data catalog databse tables ( metadata )
- these metadata can be used by 
    - Glue Jobs (ETL)
    - Athena
    - Redshift

# Neptune

- Fully manged graph database
- high relationship data
- higly available 3 AZ with up to 15 read replicas
- point in time recovery,continuous backup to s3

# ElasticSearch
- elastic search any field, even partially matches
- common use ElasticSearch as complemntto another database
- used for big data appplications
- can provision cluster of instances
- build in integrations with
    - Kinesis data firrehose
    - AWS IoT
    - Amazon Cloud watch logs
- comes with Kibana ( visualization ) and logstach ( log ingestion ) **ELK stack**









