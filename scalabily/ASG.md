![[Pasted image 20221101113842.png]]
# Auto Scaling Group

## TLDR
A Group of [[EC2]] Instances scaled horizontally, can use an [[ELB]] or work without it if there is no incomming traffic. Can use [[ELB]] or [[EC2]] health checks. Can also be used for [[ECS]] in which case it uses a ecs service as target.

## Features
- scale horizontaly
- scale out and in
- ensure maximum and minimum ec2s
- automaticly register EC2 with load balancer
- if instance is unhealthy it will be terminated and recreated
- set desired capacity

## Launch template
- similar to launch config
- specifies same stuff
- allows for multiple versions of a template
- can mix on demand and spot instances

## Launch configuration
- defines instace configuration (size etc)
- AMI
- instance Type
- key pair
- [[SecurityGroup]]
- block device mapping
- can not be modified but must be swaped if already in use

### [[EC2]] Tencacy
- dedicated before other configs
- Take [[VPC]] tenacy config into account

## Instance States

### Standby
- used for maintance
- wont be terminated if health check fails
- wont recieve traffic

## Termination Order
1. Cost (Spot vs on-demand)
2. oldest launch configuration
3. oldest launch template
4. closest to next billig hour

## Scaling Policies

### Simple
- scale by threshhold values
- must wait for scaling and health check to complete to scale again
- must wait for cooldown period expide to scale again

### Step
- scale by multiple threshold values to different configs

### Scheduled
- scale on predefined time window

### Target Tracking
- scale to match the defined metric (e.g. 50% cpu)
- must not wait for cooldown period

## Scaling Actions

### Rebalancing
Happens when an instance is missing or AZ is changed or Spot schenanigans.
1. Launch new instances
2. Terminate old instances

### Scaling
Happens for health checks
1. Terminate
2. Launch new

