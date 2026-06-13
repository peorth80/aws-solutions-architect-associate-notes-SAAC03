![[Pasted image 20221031111307.png]]
# VPN

## TLDR
Access AWS Resources in one or more [[VPC]]s as if they were in your on premise network.

## Design
- Use non-overlapping ip ranges for each network
- Use Transit Gateway to increase throughput for a single site, this allow multipath routing using aditional vpn tunnels

## Options

### AWS Managed VPN
- over internet
- aws managed
- use this to take advantage of aws managed services for failover and redundency
- one Virtual Private gateway to multiple Customer Gateways

#### Pro
- reuses existing vpn equipment
- reuses existing internet connection
- highly available
- Static routes, Border Gateway Protocol, peering and routing policies
- single [[VPC]] target

#### Cons
- Network latency
- variablity
- depending on internet
- Customer managed enpoints need to implement failover manually
- Customer device needs single hop BGP

### AWS Transit Gateway + VPN
- over internet
- aws managed
- regional router distributes traffic to different [[VPC]]
- vpc need to be in the same region
- multiple customer gateways for one AWS Transit Gateway

#### Pro
- Same as AWS Managed VPN
- additional high availabilty and scalabity 
- up to 5k attachments for the transit gateway

#### Cons
- same as AWS Managed VPN

### AWS [[DirectConnect]]
- Dedicated network connection over private lines
- Uses [[VirtualInterfaces]] in addition to customer gateway
- need multiple aws direct connect connections to support multiple customer entrypoints, but only one virtual private gateway on AWS side
- higher bandwidth
- using private ip
- 1 to 10 Gbps
- can use link aggregation group
- Use direct connect transit Gateway to connect to multiple regions or accounts or [[VPC]]

#### Pros
- More predictable Network performance
- Reduced bandwidth costs
- Support BGP peering and routing policies

#### Cons
- Requires additional telecom infrastructre
- Time to install (~2 weeks)

### AWS Transit Gateway + AWS [[DirectConnect]]
- dedicated private network connection to region router which distributes the traffic to multiple vpcs

#### Pros
- Same as AWS [[DirectConnect]]
- additional high availabilty and scalabity 
- up to 5k attachments for the transit gateway

#### Cons
- Same as AWS [[DirectConnect]]

### AWS [[DirectConnect]] + VPN
- Ipsec VPN connection over private Lines

#### Pros and Cons
- all Pros and cons of AWS Mangend VPN and AWS [[DirectConnect]]

### AWS [[DirectConnect]] + VPN + Transit Gatway
- Same as AWS [[DirectConnect]] + VPN but for up to 5k targets

### AWS VPN Cloud Hub
- Connect remote branch offices in a hub-and-spoke model for primary or backup connectivity
- Connect remote to remote to remote to vpn

#### Pros
- Reuses existing internet connection and AWS VPN connections
- AWS managed and highly available
- Supports BGP for exchanging routes and routing policies

#### Cons 
- Network latency
- variablility and availabilty are dependend on internet
- User managed branch office endpoints are responsible for failover implementation

### Software Site to Site VPN
- Software applicance-based VPN connection over the internet

#### Pros
- supports wider range of VPN vendors, products and protocols
- Fully customer manged solution

#### Cons
- customer is responsible for implementing high availabilty for all endpoints

## IPSec
- also known as Site to Site VPN
- connect to a vpc from on premise/remote

### Virtual Private Gateway
- also known as VPN Gateway
- entrypoint to AWS [[VPC]] side of your VPN Connection

### VPN Tunnel
- encryted link where data can pass from the customer network to, or from aws

### Customer Gatway
- An AWS Resource that provides Information to AWS about your Customer Gateway device

### Customer Gateway Device
- Physical or Software
- On customer side (on premise/remote) to establish VPN connection


