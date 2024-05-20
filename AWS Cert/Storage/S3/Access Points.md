*Allow groups of users to access certain places in the S3 bucket (allowing organization and lower prefix calls)*

- $ Simplifies security management for buckets
- $ Unique DNS name for each AP (Internet Origin or VPC Origin)
- $ Unique access point policy

![[Screenshot 2024-04-21 at 2.57.38 PM.png]]

# VPC Origin
- Must create a VPC endpoint (Gateway or Interface Endpoint)
- VPC Endpoint Policy must allow access to the target bucket and Access Point
![[Screenshot 2024-04-21 at 3.01.38 PM.png]]