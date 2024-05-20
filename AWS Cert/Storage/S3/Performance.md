- S3 Automatically scales to high request rates, latency 100-200 ms
- Can achieve 3,500 PUT/COPY/POST/DELETE or 5,500 GET/HEAD requests per second per prefix in a bucket
# S3 Prefix
*The "Parent directory of a file (not including bucket name)"*
e.g.

| Object Path              | Prefix         |
| ------------------------ | -------------- |
| bucket/folder1/sub1/file | /folder1/sub1/ |
| bucket/1/file            | /1/            |
# S3 Transfer Options
## Multi-Part upload
*Divides the file Into multiple parts to allow parallelization of uploads to the bucket*
- ! Recommended for files > 100MB
- !! Must be used for files > 5GB
- $ Parallelizes uploads (faster transfer speeds)

![[Screenshot 2024-04-21 at 1.39.26 PM.png]]

## S3 Transfer Acceleration
*Transfers file to an AWS edge location which then forwards the data to the bucket in the target region*
- $ Compatible with multi-part upload
- $ Limits public network access and maximizes private AWS network

![[Screenshot 2024-04-21 at 1.42.41 PM.png]]

## S3 Byte-Range Fetches
*Parallelize GETs by requesting specific byte ranges*
- $ Speeds up downloads
- $ Can be used to retrieve partial data
- $ Beter resilience in case of failures

![[Screenshot 2024-04-21 at 1.44.47 PM.png]]