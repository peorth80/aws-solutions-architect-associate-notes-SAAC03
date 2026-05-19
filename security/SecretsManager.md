# Secrets Manager
- vs SSM newer, force rotation every x days, automate generation of keys
- integration with rds
- secrets can be encrypted using kms

## Rotate Keys
- To rotate keys, you can use a custom Lambda function

## Multi Region Secrets
- replicate secret accros regions
- creates replica secrets
- can promote replica secrets to master
- used for disaster recovery of rds e.g.