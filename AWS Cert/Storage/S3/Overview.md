# Definitions
## Bucket
*Top level directory*
- Must have a globally unique name (across all regions and all accounts)
- Defined at the **region level**
- 
## Object
*Files in the [[#Bucket]]*
- Files have a key (full path of the file)
- Example key: s3://my-bucket/file.txt
- prefix + object name
- Keys are not paths (like a directory) but just a key that can contain "/"
- Max object size is 5TB
- Uploading > 5GB must be multi-part upload
- Other info
	- Metadata - text key / value pairs for system or user metadata
	- Tags - unicode key / value pair (up to 10) 
	- Version ID - For versioning
- 
# Durability/Availability
## Durability
*Chance of loss of object over time*
99.9999999% durability
## Availability
*Chance object/service is readily available*
99.99% availability