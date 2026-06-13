![[Pasted image 20221101124548.png]]
# RDS

## TLDR
Various relational databases, managed by aws.

## Features
- scaling capacity (up to set maximum storage, every 6h max, 5 mins needs to be low storage which is less than 10% remaining) this needs to be enabled.
- os patching
- no ssh
- monitoring dashboards
- multi az
- scaling capability

## Read replicas
- up to 5 read replicas
- eventually async replication
- can be promoted to their own database
- no cross az network cost
- cross region cost per network traffic
- can be multi AZ

## Multi AZ
- can be upgraded without downtime
- one dns name
- automatic failover to standby database by switching target ip or dns name
- sync replication
- one db will be standby
- deactive automation mode and take snapshot before modify
- automated backups will be multi region

## RDS Custom
- only for oracle and mssql
- access to underlying database and os
- ssh possible

## Security
- if you need encrypt in transit use ssl/tls by launching the client with the --ssl_ca flag
- can use [[KMS]] to encrypt data at rest

### Option

#### RDS Custom for Oracle
- allows customization to host and os

## Maintenance
- maintenence causes downtime even if the db is multi AZ

## Backups
- daily full backup during maintence window
- transactions logs are backed up by rds every 5 mins
- restore any point in time (5 mins ago)
- 1 to 35 days of retention
- if multi az backups span multi region

### Manual Snapshot
- manual trigger
- retention as log as you want
- pay for the space occupied

### Savings
- take snapshot and delete database
- if you want rds back just restore with snapshot

### Restore
- restore mysql rds database from [[S3]]

## Security
- encrypt at rest with [[KMS]], must be defined at launch time
- if master is not encrypted, read replicas can not be encrypted
- to change from and to encypt use snapshot
- encrypt in flight with tls root certificates client side
- can use [[IAM]] roles to connect to database instead of username and pw on mySQL-compatible DBs
- can use [[SecurityGroup]]
- audit logs can be enabled and be send to [[CloudWatch]]


## RDS Proxy
- fully manged database proxy 
- allows apps to pool and share connection established with the database which allows less connections to database
- improves database performance
- severless
- autoscalling
- high available (multi az)
- reduces rds and aurora failover time by 66%
- enforces iam auth for db and store creds in aws secrets manager
- RDS Proxy is never public and can only be used from within the vpc

## Enhanced Monitoring
[[CloudWatch]] feature for RDS
- RDS child processes
- RDS processes
- OS Processes
