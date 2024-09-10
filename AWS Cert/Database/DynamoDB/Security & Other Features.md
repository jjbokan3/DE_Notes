# Security
- $ VPC Endpoints allows DynamoDB to be accessed without using the internet
- $ Access controlled by IAM
- $ Encryption at rest using AWS KMS and in transit using SSL/TLS

# Backup and Restore
- Point-in-time Recovery (PITR) like RDS
	- $ No performance impact

# Global Tables
- $ Multi-region
- $ Multi-active
- $ Fully Replicated
- $ High Performance

# DynamoDB Local
*Allows you to locally utilize the DynamoDB features for development*
- $ Allows you to develop and test apps without internet

# [[Database Migration Service]]
- $! Allows you to migrate data from other services (MongoDB, Oracle, MySQL, S3) to Dynamo

# Temporary Access
*Allows users access to DynamoDB without having to assign a new role/credentials*
- $ Users login through Google, Facebook, Amazon Cognito User Pools
	- ! They are granted temporary AWS credentials and an IAM role
- ! Permissions are restricted based on the `Condition` value in the role

## Data Scoping

| Variables   | Info                                                              | Example                                                                               |
| ----------- | ----------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| LeadingKeys | Limits the user to access row-level data based on the Primary Key | User can only access their own data based on their id that appears in the primary key |
| Attributes  | Allows the user to only see certain attributes                    | Only allow the user to view important information to their request                    |
