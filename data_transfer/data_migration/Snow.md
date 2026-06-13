![[Pasted image 20221031104435.png]]
# AWS Snow Family

## TLDR
The Snow Familiy is a collection of **hardware** which can be used to transfer large amounts of data into or out aws. Alternatively this hardware can also be used as data storage and computing power in locations where there is not internet (Edge).

## Data migration
- Used when network lines are not fast enough (TBS and PBS)

### Step by Step
- Request a device from aws
- Install ops software on your servers
- Use the client and hardware
- Ship back
- Snow device is wiped

## Devices

### Snowball Edge
- big box to move tb or pbs of data in and out of aws
- pay per job
- provide block or [[S3]] compatible storage
- cluster up to 15 devices (like 1 PB)

#### Storage optimized
- 80 TB

#### Compute optimized
- 42 TB 

### Snowcone
- smaller Snowball
- 8TBs of storage
- fits on top of a drone
- can transfer via network as well (collect offline transfer online)

### Snowmobile
- truck to transfer data
- 100PB of data
- high security
- use when transfering more than 10 PB

## Edge Computing
- process on edge
- no internet access
- preprocess

### Snowcone
- 2cpus, 4gb on memory

### Snowball Edge
- runs [[EC2]] or [[Lambda]] functions

#### compute optimzed
- 52vCpus 208GiB Ram

#### storage optimized
- up to 40 vCpus, 80GiB of Ram

## Ops Hub
- GUI Software to connect to snow devices
- edge computing 
- store data for transfer