---
title: Microsoft AD
date: "2020-09-10T16:01:00.000Z"
description: "Microsoft AD"
---

# Microsoft Active Directory
- found on any windows server with AD Domain services
- database of objets
    - users accounts
    - printers,
    - file shares
    - security groups
- centralized security management, create account, assign permissions
- objects are organized in **trees**
- group of trees is a **forest** 

## AWS Directory Services
- Managed Microsoft AD
    - Create your own AD in AWS, manage users locally, support MFA
    - Establish "trust" connections with your on-premise AD
- AD Connector
    - Directory Gateway (proxy) to redir3ect to on-premise AD
    - Users are managed on the on-premise AD
- Simple AD
    - AD-compatible managed directory on AWS
    - cannot be joined with on-premise AD
    