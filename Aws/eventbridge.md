---
title: Event Bridge 
date: "2020-09-10T16:01:00.000Z"
description: "Event Bridge"
---

# Event Bridge
- next evolution of cloudwatch events
- Cloudwatch events uses default event bus
- Event bridge can have many event bus
    - Parner event bus
        - events from SaaS servie or applications
        - Zendesk, DataDog, Segemnt, AuthO
    - Custom events
        - from your own applications
- Event buses can be accessed by other AWS accounts
- **Rules** - how to process events 

## Schema Registry
- EventBridge can analyze the events in your bus and infer schema
- Schema Registry allows you to generate code for your application that will know in advance how data is structure in the event bus
- Schemas can be versioned
