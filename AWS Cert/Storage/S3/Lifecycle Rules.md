*Thresholds for moving objects to more cost-efficient [[Storage Classes]]*

# Definitions
**Transition Actions** - Configure objects to transition to another storage class
**Expiration actions** - Configure objects to expire (delete after some time)
- Delete after X days
- Delete old versions of files (with [[Versioning]])
- Delete incomplete Multi-Part uploads

## Current vs Non-Current
-  Current are objects of the most recent version
-  Non-Current includes older versions as well as DELETE MARKERS

## S3 Analytics
- Helps you decide when to transition objects
- CSV report will recommend between Standard and Standard IA

Possible directions
![[Screenshot 2024-04-21 at 12.30.52 PM.png]]
![[Storage Classes#Lifecycle Rules#Setup]]
# General Notes
- ! Rules can be created for a certain prefix (s3://mybucket/mp3/*)
- ! Rules can be created for certain object Tags (Department: Finance)