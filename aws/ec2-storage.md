---
title: EC2-Instance Storage
date: "2020-09-01T03:47:00.000Z"
description: "EC2 Instance Storage"
---

# EC2 Instance Strorage

## EBS - Elastic Block Store

- Can be attached to instance while they run
- Used to persist data even after instance termination
- **Bound to Avalablity zone**
- Can only be mounted to one instance at a time 
- Can only be attached to instance in same avalability zone
- **Network Drive** not a physical drive 
    - can have latency since it is network drive
- To move data across multiple AZ need to to **snapshot**
- can be created during the intance creation
    - there is a option to **delete on termination** if required
- can be encrypted or not encrypted
- 6 Types
    - gp2/ gp3 - general purpose ssd volumns 
        - balanced price and performance
    - io1/io2 
        - low latency , high throught put workloads
    - st1 -  low cost hdd volumn designed for frequently accesssed, throughtput intensive workloads
    - sc1 - lowest cost volumn designed for frequently accesssed workloads

>**Only gp2/gp3 and io1/io2 can be used as boot volumns**

### Provisioned IOPS (PIOPS) SSD

- Application that need more than 16000 IOPS
- eg: database work loads
- io1/io2
    - max PIOPS : 64000 for Nitro Ec2 Intances and 32000 for others
- io2 - Block Express
    - sub millisecond latency


 ### EBS snapshots

 - backup at any point of time
 - not necessary to detach volumn to do snapshot, but recommended
 - can copy snapshots acrosss AZ or region

 ### EBS Multi Attach - io1/io2 family
 - Attach the same EBS volumn to multiple EC2 instances in the same AZ
 - EC2 will have full read and write
 - Must use a cluster aware file system ( not XFS, EX4, etc...)


 ### EBS RAID Options
 - used when IOPs has to be increased
 - if u want to mirror EBS volumns
 - supported if OS supports it
 - RAID Options
    - RAID 0
        - increse peformance ( no replication )
        - if a disk is failed data is lost

    - RAID 1
        - increase falt tolerance
        - if a disk is failed data can be recovered from the other
        - 2x network usage :: because 2 copies
    - RAID 5 ( not recomended for EBS )
    - RAID 6 ( not recomended for EBS )
- RAID configurations has to be done in the OS level ( not available in console )


## EC2 Instance Store

- Used for better IO performance ( high performance )
- data will be lost when u restart instance
- can be used for buffer, cache...
- Only present in certain type of instances ( instances which starts with i )


## EFS - Elastic File System
- Managed NFS
- **can be mounted on may EC2**
- **can be mounted acrosss AZ**
- **3 times the cost** of EBS (gp2)
- pay per use ( size not provisioned during creation )
- **security groups to control access** 
    - type NFS
    - Source **reference to the ec2 security group**

- only on linux based AMO ( not windows )

- Performance Mode
    - General Purpose: ( default ) latency- sensitive use case ( web server,CMS...)
    - MAX I/O - higher latency, throughput, higlly parallel ( big data, media processing )
- Throghtput Mode
    - Busting ( 1 TB = 50 MiB/s + burst of up to 100MiB/s )
    - Provisioned - throughput regardless of storage size eg: 1GiB/s for 1 TB storage
- Storage Tiers ( lifecycle manangement feature - move file after N days )
    - standard: for frequent accessed files
    - infrequent access (EFS-IA): cost to retrieve files, lower price to store







