![[Pasted image 20221101210003.png]]
# VPC Virtual Private Cloud

## TLDR
A stack of AWS resources, more clearly the connectivity and setup options for and between these resources.

## Console Wizard

### Options

#### VPC with public subnet
- single public subnet
- internet gateway
- recommended for simple public facing application

#### VPC with public and private subnets
- public subnet
- private subnet
- internet gateway
- recommended for 2 tier application

#### VPC with public, private subnets and AWS Site-to-Site [[VPN]]
- public subnet
- private subnet
- virtual private gatway
- internet gateway
- recommended to extend network into the cloud and some resource are internet facing

#### VPC with private subnet and AWS Site-to-Site [[VPN]]
- private subnet
- virtual private gateway
- recommended to extend private network into the cloud

## VPC Endpoint
- privatly connect a VPC to supported services 
- does not require an internet gateway, [[NAT]], [[VPN]] or [[DirectConnect]]
- instances dont require public ip adresses
- uses AWS Private Link as connection Line
- data does not leave AWS while communicatiing
- doesn not support inter region communication

### Interface Endpoint
- Connect to services without passing through the internet (IE, SQS, SNS, etc)
- ENI with private ip address in the target subnet
- Hast cost

### Gateway Endpoint
- only for [[S3]] and [[DynamoDB]]
- gateway which you set as a route target 
- Free

## VPC Peering
- connection between 2 VPCs using private addresses
- not transitive (you have 3 VPC you need VPC-A -> VPC B, VPC B -> VPC C, VPC-A -> VPC-C, etc)
- need to setup route tables

### Transit Gateway
- hub for multiple peering connections
- attach options are, vpc, direct connect gateway or another transit gateway either as peering or vpn
- MTU = max package size
- MTU 85kbs if direct connect or peering vpc
- MTU 15kbs if [[VPN]]
- has a route table
- route propagation
- gives double throughput of virtual private gateway by using ECMP support

## VPC Sharing
- share one or more subnets within other accounts beloning to the same [[AWSOrganisations]]
- every account can only work with the resources they created

## VPC Flow Logs
- Capture Information about IP traffic through your interfacines
- VPC Flow Logs
- Subnet Flow Logs
- ENI Flow Logs

### Other Sources
- [[ELB]]
- [[RDS]]
- [[ElastiCache]]
- [[Redshift]]
- WorkSpaces 
- NATGW
- Transit Gateway
...


### Targets
- [[S3]]
- [[CloudWatch]] Logs
### Information
- ip information
- port information
- action (accept/reject)

### Query
- [[S3]] Athena
- [[CloudWatch]] Logs Insights

## NACL
- not stateful
- firewall on subnet level
- for outbound traffic allow ephemeral ports 32768-65535 (all ports for diffrent services to listen for outbound traffic)

## VPC Traffic Mirroring
- capture and inspect network traffic
- unintrusive
- traffic gets direct to security applicance fleet
- fleet redicet traffic back