![[Pasted image 20221031103642.png]]
# Database Migration Service

## TLDR
Migrate an existing database into another one. Can also do DB schema conversion.

## Features
- seamlessly migrate
- full set
- resilient
- self healing
- data change capture
- no code needed
- replication instaces for scaling workloads
- support continous repication
- uses an [[EC2]] instance to run dms software
- if target is [[S3]] it generates csv
- can use in transit encrypt by add ca cert to endpoint

## Sources
- On premise databases
- [[EC2]] instances
- Azure
- [[S3]]
- [[Aurora]]
- [[RDS]]

## Targets
- on premise and [[EC2]] instances
- relational Databases
- [[OpenSearch]]
- [[DynamoDB]]
- [[DocumentDB]]
- Data Warehouses
- Streaming Platforms
- [[Kinesis]]
- Amazon Manged Streaming of Kafka [[MSK]]
- [[Redshift]]
- [[Redshift]]

## Limitations
- Transfer from Aws service to aws service. Sometimes but not always (e.g. RDS) needs to be in the same region and same account

## Basic Schema copy
- Create tables and indexes
- Heterogenus migration (Oracle to MySQL e.g.)

## Schema conversion tool
- Transfer DB from one schema to another
- Move stored procedures as well

## [[RDS]] to [[Aurora]] MySQL

### Option 1
- DB Snapshot from [[RDS]] restore as new [[Aurora]]

### Option 2
- Create an [[Aurora]] read replica from [[RDS]], when replication lag is 0 promote the replica to own DB cluster

### Option 3 external to aws
- Use percona xtrabackup and upload to [[S3]]
- Create [[Aurora]] from [[S3]]

### Option4 external to aws
- Create [[Aurora]]
- Use mysqldump to migrate into [[Aurora]] (slower than s3 method)

### Option 5 
- use [[DMS]]

