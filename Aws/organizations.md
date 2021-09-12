---
title: Oranizations 
date: "2020-09-10T21:01:00.000Z"
description: "Organizations"
---

# Oranizations
- Global service
- Alows to manage multiple AWS accounts
- The main account is the master account- you cannot change it
- Other accounts are member accounts
- Member accounts can only be part of one organization
- Consolidated Billing accross all accounts - single payment method
- Pricing benefits from aggregated usage
- API is available to automate AWS account creation
- can create different Orgnizational units to separate difffent departments
    - Sales, Retail, Finanace

## Service Control Policies
- Whitelist or Blacklist IAM actions
- Appied at the OU or account level
- Does not apply to the master account
- is applied to all the Users and Roles of the Account, including Root
- SCP does not affect service-linked roles
    - service linked roles enable other aws services to integrate with AWS organizations and cant't be restricted by SCP;s
- **must have explict Allow** does not allow anything by default
- usecase
    - restrict access to certain services ( cant use EMR )
    - enforce PCI compliance by explicity disabling services

> Hirarchical Permissions - if deny present in parent, even if allow present in child. it will be deny


