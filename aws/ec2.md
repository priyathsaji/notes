---
title: EC2
date: "2020-09-01T00:37:00.000Z"
description: "EC2 Notes"
---

# EC2 - Elastic Compute Cloud

Virtual machines on demand.

Infrastructure as a Service


>default user : **ec2-user**


Different Types of Ec2 Instances
1. General Purpose ( webserver or code repository )
2. Compute Optimized ( batch processing, HPC ...)
3. Memory Optimized ( database, elasticache.. )
4. Accelerated Computing 
5. Storage Optimized ( oltp systems, databases,distributed files systems )
6. Instance Features
7. Measuring Instance Performance

Naming Conventions of EC2

> m5.2xlarge

- m -> Instance class
- 5 -> Generation 
- 2xlarge -> size within instance class

## Security Groups 

How trafic goes in and out of EC2. Firewalls on ec2.

They regulate
1. Access to ports
2. Authorized IP ranges - IPv4 and IPv6
3. Control of inbound network ( from other to the instance )
5. Control of outbound network ( from the instance to other )



### Security groups - Good to know
1. Can be attached to multiple instances
2. Live outside EC2 if blocked EC2 wont see it.
3. by default all **inbount traffic is blocked** and **outbound trafic is authorized**
4. Security group can reference other security groups ( maninly used in load balancer usecases)




> **To access other aws service always use IAM role** ( dont use access and secret keys )



## Purchasing options

1. On-Demand Intances: short work load, predictable pricing
2. Reserved (Minimum 1 year)
    1. Reserved Instances : long work loads
    2. Convertible Reserved Instances: long work loades with flexible instances
    3. Scheduled Reserved Intances: (eg: every Thursday between 3 and 6 pm)
3. Spot Intances: short workloads, cheap , can lose instances ( less reliable )
    - up to 90% cost savings
    - define a max spot price 
    - when lossing instance 2 mins grace period to stop or terminate
    - can lose instance if the price u r willing to pay is less than the current spot price
    - not sutable for critical tasks
    - spot block instance during specified time frame ( 1 to 8 hours) without interuptions. in rare situation it may be reclaimed 
    - spot requests can be 
        - persistant - restarted once spot price is below the set price
        - on-time - if lost then lost
    - termination required spot request and terminte instances manually
    - spot fleets
        - set of spot instances + optional on-demand instances
        - spot fleet will try to meet the target capacity with price constraints
        - spot fleet allocation strategies
            - lowest price : from pool with lowest price ( cost optimization, short workload)
            - diversifed : distributeed across al pool
            - capcity optimized : pool with optimal capacity for the number of instances
4. Dedicated Hosts : book and entire physical server, control instance placement
    - compliance requirements
    - use existing servr-bound software licenses
    - 3 year reservation period
5. Dedicated Intances
    - Instances running on hardwared dedicated to you
    - May share hardware with other instances in same account
    - No control over instance placement


## Elastic IP
- to have a fixed ip when u start and stop EC2 instance
- can be attached to one instance at a time
- own it as long as u dont delete it


## Placement Groups
- when instances are placed in aws
- 3 strategies
    - Cluster  - instances into a low latency group in a single Availablity Zone
        - in same rack
        - if rack fails all instances fail
        - used if the latency between instances has to be very low
    - Spread - spread instance across underlying hardware ( crital applications )
        - instances can spread across multiple Availably zones
        - limited to 7 instances per AZ per placement group
        - used for application with high availablity
    - Partitions - spred instance across different partitions ( which rely on differnt set or racks ) within an AZ. Scales to 100s of EC2 instances per groups ( Hadoop, Cassandra, Kafka )
        - partitions basically means racks
        - upto 7 partitions per AZ
        - can span across multiple AZs in the same region


## Elastic Network Interfaces - ENI
- logical component in VPC that represent virtual network card
- ENI can have
    - Primary private IPv4, one or more secondary IPv4
    - one Elastic IP per private IPv4
    - one or more security groups
    - can attach a mac address
- Bound to specific avaiblabilty zones
- create and attach ( on the  fly ) ENI independently 
- Used mainly on network fail overs

## Hibernate
- all in-memory state is preserved
- instance boot is faster
- all ram data is dumped to EBS volumn
- root EBS volumn must be encrypted
- used when the instance will take long time to initialized
- cannot hibernate for more than 60 days


## EC2 Nitro
- next genertion ec2 instances
- new vertualization technology
- better networking options 
- **higher speed EBS**
- better underliying security







