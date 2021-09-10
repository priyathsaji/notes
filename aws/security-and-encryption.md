---
title: Security And Encryption 
date: "2020-09-10T21:01:00.000Z"
description: "Security And Encryption"
---

# KMS - Key Management Service
- Easy way to control access to your data, AWS manages keys for us
- fully integrated with IAM for authentication
- seamlessly integrated with most of the aws services
- can be used with CLI and SDK
- Types of keys available in KMS
   - Symmetric (AES 256)
       - we cannnot have access to the key unnecrypted ( must call KMS api to use )
       - most of the services use these kind of keys
   - Asymetric Keys ( RSA and ECC key pairs)
       - sigin and verify operations
       - public key is downloadable, can't access private key unencrypted
       - used case : encryption outside of AWS by users who can't call the KMS API
 - able to full manange key and policies
    - create
    - rotation policies
    - disable
    - enable
- able to audit key usage ( using cloud trail )
- three types of Customer Master Keys ( CMK )
    - AWS Managed Service Default CMK : free
    - User Key created in KMS: 1$/month
    - User Key imported ( must be 256-bit symmetric key): 1$/month
- KMS can only help in encrypting up to 4KB of data per call
- if data is greater than 4KB use envolope encryption
- **region specific**
- access to kms key is provied by KMS policies
- default KMS policy
    - created if you dont privide a specific KMS key policy
    - complete access to the key to the root user =  entire AWS account
    - give access to the IAM policies to the KMS key
- custom KMS key policy
    - define user, roles that can accesss the KMS key
    - Define who can administer the key
    - Useful for cross-account access of your KMS key
    

## KMS key rotation
- can be enabled for customer managed CMK
- if enabled: automatic key rotation happens every year
- Previous keyh is kept active so you can decrypt old data
- New key has the same CMK ID ( only the backing key is changed )
- manual rotation can also be created 90 days , 180 days etc
    - new key has a different CMK ID
    - keep the previous key active so you can decrypt old data
    - Better to use alias in this case ( to hide the change of key for the application ) 
        - this has to be done manually
            - once new key is created
            - change the alias using UpdateAlias API


# SSM Parameter Store
- secure storage for configuration and secrets
- optional seamless Encryption using KMS
- Serverlesss, scallable, durable, easy SDK
- version tracking for configuration/ secrets
- Configuration management using path and IAM
- to store in parameter store
     - create a hierarchy
        - like
            - /my department
                - /my-app
                    - /dev
                        - db-url
                        - db-password
                    - /prod
                        - db-url
                        - db-password
        - path to retrieve the key
- **parameter Polices ( only available for advanced paramter ( not free ))**
    - Allow to assign a TTL to a parameter to force updating or deleting sensitive data such as passowords
    - can assign mulitple policies at a time


# AWS Secrets Manager
- Meant for storing secrets
- **can force rotation of secrets** for every X days
- Automate generation of secrets on rotation ( uses lambda )
- Integration with Amazon RDS ( MySql , PostgreSQL , Aurora )
- Secrets are encrypted using KMS
- mostly meant for RDS integration

# Cloud HSM ( Hardware security Module )
- KMS : AWS manages the software for encryption
- CloudHSM: AWS provisions encryption hardward
- Dedicated Hardware ( HSM - Hardware Security Module )
- tamper resistant
- supports both symmetric and asymmertic encryption
- has to use CloudHSM software to manange keys and users

# Sheild 
- protection agains DDos attacks
- Aws Shield Standard
    - Free service activated for every Aws customer
    - provides protects from attacks such as SYN/UDF Floods, Reflection attacks and other layer 3/layer 5 attacks
- Aws Shield Advanced
    - Optional DDos Mitigation service ( 3000 $ per month per organization)
    - protection against more sophisticated attacks
    - 24/7 access to aws DDos response team 
    - protect against highter fees during usage spikes due to DDos 

# Web Application Firewall - WAF
- Protects web application from common web exploits (HTTP layer 7)
- deploy on 
    - Application Load Balencer
    - API Gateway
    - CloudFront
- Define Web ACL ( Web Access Control List )
    - Rules can include : IP addresses, http headers, http body, URI strings
    - protects against common attack - SQL injection and cross site scripting
    - size constraints, geo - match
    - rate based rules ( count occurences of events ) - for DDos protection

## AWS Firewall Manager
- Manage rules in all accounts of an AWS organization
- Common set of security rules
- WAF rules 
- AWS Shield Advanced 
- Secrurity groups for EC2 And ENI resources in VPC

# GuardDuty
- intelligent thereat discovery to protect AWS account
- uses machine learning algorithms, anomaly detection, 3rd party data
- one click to enable,no need to install software
- input data includes
     - cloud trail logs
     - vpc logs
     - dns logs
- can set up cloud watch event rules to get notfied on findings
- cloudwatch event rules can target AWS Lambda or SNS
- can protect agains cryptoCurrenty attack ( has a dedicated finding for it )

# Inspector
- automated security accessments on **EC2**
- analyize the running OS against known vulerablities
- analyze against unintended network accessiblity
- AWS inspector agent must be installed on OS in EC2 instances
- get a report with list of vunerablities
- Possiblity to sent notifications to SNS
- evaluate 
    - Network ( agentless) - network reachablity
    - host assesment 
        - common vulnerablities and exposures
        - center for internete security benchmarks

# Macie
- Amazon macie is a full managed data security and data privacy service that user machine learning and pattern matching to discover and protect your sensitive data in AWS
- macie helps identify and alert you to senstive data, such as **personally identifialble inforamation - PII**  
