---
title: Route 53
date: "2020-09-02T02:25:00.000Z"
description: "Elastic Cache"
---

# Route 53

- Managed DNS
- A Record
    - hostname to IPv4 address
- AAAA
    - hostname to IPv6 address
- CNAME
    - hostname to hostname
    - only works for none root domains
        - eg : somthing.mydomain.com
- ALias
    - hostname to aws service
    - works for both root and sub domain
    - free of charge
- load balencing
- health checks
- routing policy
- global service not region

## TTL 
- caching time by browser once address is fetched from DNS
- this is done so as not to overload dns
- default value in route 53 is 300

## Health check
- if health check failed route 53 wont sent the request to that instance
- unhealty by if failed 3 health checks
- can be HTTP, TCP  and HTTPS health checks
- can be integrated to Cloud watch
- default health check interval 30s

## Routing Policy
- simple routing
    - when routing to a single resource
    - cannot attach health checks to routing policy
    - can return mutiple values to browser - browser chooses one random from the list
- Weighted Routing
    - assign weight to different end points
    - routing based on weightage given to different endpoints
    - multiple recodes in route 53 with same domain name ( different weights )
- Latency Routing
    - routed to the least latent endpoint of the user
    - similare to weighted routing has to create multiple records in route 53 
- Failover Routing
    - tag it to a health check 
- GeoLocation routing
    - route based on user location
- Geoproximity routing
    - user location and a bias value
    - use a bias value to shift the regions
- MultiValue Routing policy
    - when routing traffic to multiple resources
    - associate route 53 healt checks with records
    - route 53 returns all the endpoints which r health
    - browser decides where to be routed

## Route53 as a Registrar
- an organization that manages the reservation of Internet domain names
- place where we by domain names
- can use domain names brought from other registars in route53
    - for this have to update name servers in the registrar with aws name servers
    - name servers can be fetched from the details of hosted zones








