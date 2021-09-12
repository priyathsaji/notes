>
# AWS Config
- helps with auditing and compiance of aws services
- help record configurations and chagnes over time
- can solve
    - is there unrestricted ssh access to my security groups
    - do my buckets have any public access
    - How my ALB configuration changed over time
- can recieve alerts for any changes
- per region service
- can be aggregated accross regions and acconts
- storign configuration data into s3 ( analysed by athena )

## Config Rules
- can use AWS managed config urls ( over 75 )
- can make custome config rules ( must be defined in AWS lambda )
    - evaluate if each ebs disk is of type gp2
    - evaluate if each ec2 insstance is t2.micro
- Rules can be evaluated / trigged
    - for each config changes
    - regular intevals
- **AWS config rules does not prevent actiosn from happening ( no deny )**
- **Remediation actiosn can be done using SSM automation**
    - use aws-managed automation documents or create cutom automation documents
        - can create automation document that invokes lambda function
    - can use event bridge to trigger notifications when resources are not compliant