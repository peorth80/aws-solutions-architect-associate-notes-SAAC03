![[Pasted image 20221101164642.png]]
# Elasticache

## TLDR
Volatile Caching Layer with high performance.

## Features
- in memory data store
- boost performance of databases
- use cases caching, session stores, gaming, geospatial services, real time analytics and queuing
- for relational databases caching layer
- helps make app stateless
- aws managed (os, patching, monitoring, failure recover, backups)
- requires app changes

## Use Cases
- read heavy hpc tasks
- compute heavy hpc tasks
- session stores
- high performance db caching
- ...

## Redis
- see [[Redis]]

## Memcached
- open source memory store
- multithreaded
- no replication
- no snapshots
- no transactions
- no pub/sub
- no geosparital support
- no lua scripting
- no high availabilty
- sharding
- non persistent
- no backups
- support SASL based auth

## Security
- no [[IAM]] Auth
- can use ssl encruption for in flight

## Loading patterns
- lazy (all read data is cached, but can become stale)
- write through (adds or updates to the db are mirrored in the cache)
- session store (expire data with time to live)