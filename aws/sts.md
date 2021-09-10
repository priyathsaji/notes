---
title: STS 
date: "2020-09-10T16:01:00.000Z"
description: "STS"
---

# STS - Security Token Service
- allows limitedand temporary access toi AWS resources
- Token is valid for up to one hour ( must be refreshed )
- **Assume role**
    - Within your own account, for enchanced security
    - Cross account access, asume role in target acount to perform actions there
    - procedure
        - define IAM role within your account or cross-account
        - define principles can access this IAM role
        - Use Aws STS to retrieve credentials and impersonate the IAM role you have access to
        - temporary credentials can be valid between 15 mins and 1 hour
- **AssumeRoleWithSAML**
    -return credentials for users logged with SAML
- **AsumeRoleWithIdentity**
    - returls creds of users logged with Idp ( Facebook, google ..)
    - **AWS recomends against using this.. use cognito instead**
- **GetSessonToken**
    - for MFS, from a user or AWS account root user
