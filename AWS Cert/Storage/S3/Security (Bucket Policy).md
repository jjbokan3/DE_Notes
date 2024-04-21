# User Based
IAM Policies - Which API calls should be allowed for a specific user from IAM

# Recourse Based
**[[#Bucket Policies]]** - rules for the specific bucket, allowing other users (or the public) to access the S3 bucket

**Object Access Control List (ACL)** - finer grain
**Bucket Access Control List (ACL)** - less common

IAM principal can access an S3 object if:
- User IAM permissions ALLOW it OR the resource policy ALLOWS it
- AND there's no explicit DENY


# Bucket Policies
![[Pasted image 20240417174915.png]]
- Json based policies
	- Resources - buckets and objects
	- Effect - Allow/Deny
	- Actions - Set of API to Allow or Deny
	- Principal - The account or user to apply the policy to
- Reasons for creating
	- Public access
	- Force objects tp be encrypted at upload
	- Grant access to another account (cross account)