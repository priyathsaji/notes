---
title: CloudFront
date: "2020-09-06T08:32:00.000Z"
description: "CloudFront"
---

# Cloud Front

- content delivert Network,
- improves read permormance, cacned at the edge location,
- DDOS progrestion with aws sheild
- http and https
- support Geo Restrition
    - can restrict who has access to the content
    - whitelist or blacklist users based on their geo location
- can be routed based on orgin
    - eg: /api/ -> can be redirected to Ec2
    - eg: /images/ -> can be redirected to s3
- **origin group**
    - to increase avalability
    - one primary and one secondary
    - if primary fails , the secondary origin takes over
- **Field Level Encryption** 
    - protect user sensitive information throught application stack
    - added additional layer of security along with HTTPS
    - sensitive information encrypted at the edge close to user
    - uses asymetric encryption
    - usage
        - specify set of fields in POST request that you want to be encrypted ( up to 10 fields )
        - specify the public key to encrypt them

## Cloud Front origins
-S3 Bucket
    - for distributing files and caching them at the edge
    - enhanced security with cloudfront ( s3 access only through cloud front )
    - can be used as ingress ( to upload file to S3 )
    - need **Origin Access Identity**
        - have options to enable access to s3 only through cloudfront

- Custom Origin (Http)
    - Applicaition Load Balencer
    - EC2 instance
    - s3 website


