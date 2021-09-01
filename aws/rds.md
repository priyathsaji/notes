---
title: RDS
date: "2020-09-01T03:47:00.000Z"
description: "Relational Database Service"
---

# RDS - Relational Database Service
- managed DB service for DB with uses sql as query language
- databases supported are
    - PostGres
    - MySql
    - MariaDB
    - Oracle
    - Microsoft Sql Server
    - Aurora
- Automatic Provisioning and OS patching
- continuous backups and restor to specific timestamp
- monitoring dashboards
- read replicas for read performanc
- multi AZ for disaster recovery
- scalling capablities
    - vertical
    - horizontal
- storage backed by gp2 or io1
- trasaction logs are backed-up by RDS every 5 mins
- 7 days retetion period for backups ( up to 35 days )
- storage will auto scale if enabled up to a threshold
    - if free storage less than 10%
    - low storage last at least 5 mins
    - 6 hours have passed since last modification

> cannot ssh into underlying instances

## Read Replicas

- help scale reads
- up to 5 read repicas
    - within AZ
    - cross AZ
    - cross region
- async replication
    - eventually consitant
- read replicas can be promoted to main database
- no fee with data transfer within region

## RDS - MULTI AZ
- sync replication
- one DNS Name
- automatic fail over if main database fails
- no manual intervension
- no read and writes just used in case if main database fails
- **Read replicas can be  set up as Muli AZ for disaster Recovery**

> **Single AZ to multi AZ is zero down time operation**

## Encryption
- At rest encryption ( master and read replicas )
    - AWS KMS - AES 256 encryption
- **master has to be encrypted for read replicas to be encrypted**
- in flight encyrption with SSL
    - provided ssl options with trust certicate while connecting to database

> **IAM based login for RDS MySql And PostGreSql**
    - No need of password with authentication token obtained through IAM and RDS api calls
    - token has life time of 15 mins
    

