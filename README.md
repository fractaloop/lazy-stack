# Lazy Stack

A simple CloudFormation stack that lets Amazon do your job for you.

## VPC
* [Networking Layout](https://github.com/fractaloop/lazy-stack/blob/master/cloudformation/region.json)
* Public Subnets/DMZ - Has NAT/VPN
* AWS Subnets - ELBs, ElastiCache, RDS
* SemiPrivate Subnets - Anything with an EIP that needs direct internet routing
* Private Subnets - Anything without an EIP that goes through the NAT

## ELB
* SSL Termination for Brain, then port 80 inside the VPC.
* Use Route53 to weight between ELB endpoints for upgrades or outages. Production normally has weight of 10, but can be split 1:9 or any number of ways

## CloudFormation
* [CloudFormation Templates](https://github.com/fractaloop/lazy-stack/blob/master/cloudformation/)
* Create or re-use S3 Bucket with a subdirectory called /templates/ and upload the nat.json

## How to Setup Initial CloudFormation Environments
* Inside of AWS GUI Console - Load the global.json
* Take the SQS/SNS and feed it to the region.json into the CloudFormation GUI
