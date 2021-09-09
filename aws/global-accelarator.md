---
title: Global Accelarator
date: "2020-09-06T08:32:00.000Z"
description: "Global Accelarator"
---

# Global Accelerator
- Unicast IP
    - one server holds one IP address
- Anycast IP
    - all servers have the same IP address
    - request get routed to the nearest one

- Global Accelerator uses **AnyCast IP**
- Uses AWS internal network to route to the application
    - suppose application is hosted in a region
    - and users from other region has to access this resource
    - If u use Global Accelerator. The request can be routed through the edge locations to the resource
    - This is done to make the request faster
- works with
    - Elastic IP
    - EC2
    - ALB
    - NLB


> Cloud front caches the request, but Global Accelarator does not cache the content - Global Accelarator acts as a proxy

