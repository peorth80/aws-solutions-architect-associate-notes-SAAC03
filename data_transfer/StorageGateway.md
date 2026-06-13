![[Pasted image 20221031110419.png]]
# Storage Gateway

## TLDR
Can be used for a hybrid cloud setup, where data is produced on premise and synced to aws.

## Usage
- long term migrations
- security
- complicance
- general IT strategy (hybrid cloud)
- tiered storage
- backup and restore
- disaster recovery

## Gateway Types

### [[S3]] File Gateway
- NFS or SMB Protocol
- Translates save file request to http request to [[S3]]
- Most recently used data is cached in file gateway, so it doesnt have to be fetched from aws

### FSx File Gatway
- Native access to [[FSxWindowsFileServer]]
- Local cache for frequently accessed data
- Windows native compatiblity (SMB, NTFS, AD)
- Group file shares and home directories

### Volume Gateway
- Block Storage
- Backed by [[EBS]] snapshots

#### Cached volumes
- low latency access to most recent data

#### Stored volumes
- dataset on premise, backups are schedules to [[S3]]

### Tape Gateway
- uses Virtual Tape libray
- for backup processes using physical Tapes
- can send directly into [[S3]] Glacier

## Hardware appliance
- Can be bought from amazon.com
- Is a hardware which will be your gateway (like a firewall)