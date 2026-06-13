![[Pasted image 20221101114116.png]]
# Route 53

## TLDR
AWS Nameserver and Domain Name register Service.

## Features
- managed
- scalable
- authorative dns (can be updated by customer)
- registar (can register own names)
- 100% availabilty
- health checks


## DNS Record
- domanin name
- record Type
- value (ip)
- routing policy
- ttl

### Record types

#### A
- hostname to ipv4

#### AAAA
- hostname to ipv6

#### CNAME
- maps dns querys to another domain or subdomain
- AAAA
- CNAME
- NS

#### Alias
- can target a root domain (cname can not)
- can only be used for aws resources

## Endpoint types

### Outbound
- used by resources in [[VPC]] to resolve dns queries to resources outside of the [[VPC]]  (e.g. on premise)

## Inbound
- used by resources outside of aws to resolve name to resources inside a [[VPC]]

## Routing Types

### Weighted
- split traffic % to a % to b

### Latency based
- route to record with least latency for user