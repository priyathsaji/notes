---
title: Storage Extras
date: "2020-09-06T08:32:00.000Z"
description: "Storage Extras"
---

# Snow Family
- highly secured portable devices to collect and process data at the edge, and migrate data in and out of AWS
- time take to transfer large amount of data to aws via network might take a lot of time..
    - so use a snow family device
    - amazon sent u a device.. load data.. sent the device back

- Snowball Edge
    - for TBs or PBs of data
    - pay per data transfer job
    - 2 types
        - storage optimized
            - 80TB of HDD capacity for block volumne and s3 computable object
        - compute optimized
            - 42 TB HDD capacity
- Snowcone
    - small portable compute
    - 8TB storage capacity
    - must provide ur own battery and cables
- Snowmobile
    - Exabytes of data
    - a big truck

- Data Migration
    - Snowcone
    - Snowball edge
    - Snowmobile
- Edge computing
    - Snowcone
        - 2 cpus, 4 gb of ram 
    - Snowball edge
        - 52 vcpus, 208 GiB or fam ( compute optimized )
        - 40 vcpus , 80 GiB or ram  ( storage optimized ) 

> Ops Hub -> GUI to connect to snow family devices


# Storage Gateway
- hybrid cloud
- expose s3 data on-premise
- 3 Types
    - Files 
        - buckets accessible using NFS and SMB protocol
        - supports standard s3, s3 IA, s3 one zone IA
        - bucket access using IAM roles for each file gateway
        - most recently used files are cached at file gateway
        - can be mounted on many servers
        - can be integrated with Active Directory AD for user authentication
    - Volume
        - block storage
        - iSCSI protocol backed by s3
        - backed by EBS snapshots which help restore on-premises volumns
        - cached volumns -  low latency access to most recent data
        - stored volumns -> entire dataset is on premise, scheduled backups to s3
    - Tapes
        - to support tape based back ups
        - uses VTL - virtial Tab library backed by s3 and glacier

## Storage Gateway Harware appliance
- If on-premise harware is not available
- by it on amazon.com

# FSx for Windows
- EFS is a shared POSiX system for Linux systems
- FSx as a solution for windows
- support SMB and NTFS protocol
- Microsoft AD integration
- **FSx for Lusture**
    - parallel distributed file systemm for large scale processing
    - machine learning and HPC
    - Linux + cLUSTER => LUSTER
    - integration with s3
        - read s3 as a file system ( throught FSx)
        - can write output of the computation back to s3 ( throught FSx)
    - can be used from on-premise servers
- types
    - scratch file system
        - temporary storage
        - data is not replicated
        - high burst
        - use case
            - short- term processing, optimized costs
    - presistent file system
        - Long-term storage
        - data is replicated in same AZ
        - replace failed files in minutes
        - usecase
            - long-term processing, sensitive data 

# Transfer Family
- file transers into and out of Amazon s3 or EFS using ftp protocol
- supported protocol
    - FTP
    - FTPS
    - SFTP
- pay per provisioned endpoint per hour + data transfer cost in GB
- can be integrated with authentication systems ( microsoft AD, okta, LDAP )



