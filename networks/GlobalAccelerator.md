
# AWS Global Accelerator

![[Pasted image 20221101170746.png]]
## TLDR
UDP compatible global endpoint to speed up network traffic to your VPC by using edge locations and aws private network.

## Features
- network layer service
- distribute traffic to optimal endpoints over AWS Network
- two static anycast ip adresses as fixed entrypoints
- Global service
- can use weights to distribute portion of traffic
- good fit for non http use cases

## Targets
- [[ELB]] ALB
- [[ELB]] NLB
- Elastic IP
- [[EC2]]

## Health Checks
- failover less than 1 min unhealty
- good for disaster recovery

## Security
- only 2 external ips need to be whitelisted


