# EBS
- ^ Can connect to one EC2 instance at a time (except multi-attach io 1/io 2)
- ^ Are locked at the AZ level
- ~ gp2: IO increases if the disk size increases
- $ gp3 & io 1: Can increase IO independently 
- ~ Root EBS Volumes get terminated when EC2 instance is terminated (can be disabled)
## Migrating across AZ
```mermaid
graph LR

Take_Snapshot --> Restore_Snapshot_to_AZ
```
- ^ EBS backups use IO and shouldn't be run if application is handling a lot of traffic

![[Screenshot 2024-04-21 at 5.07.53 PM.png]]

# EFS
- $! Mounting 100s of instances across AZ
- $! Supports Network File System version 4 (NFSv4)
- ! Only for Linux instances
- ^ Higher price point than EBS
- $ Can leverage EFS-IA for cost savings

![[Screenshot 2024-04-21 at 5.07.34 PM.png]]