*Controling table's capacity (read/write)*

# Provisioned Mode
Default mode that provides a set amount of read/writes per seconds
- $ Cheaper
- ^ Need to plan ahead of time
# On Demand Mode
Read/writes scale automatically with the workflow demands.
- $ No planning ahead of time needed
- $ Pay only for what you use
- ^ Much more expensive (2.5x more expensive than provisioned)

# Writing
## WCU (Write Capacity Units)
- Represents one write per second for an item up to 1 KB in size
- ! If items are larger than 1 KB, they will use more WCU
- ! # of KBs is rounded up (2.2KB → 3KB)
- ? What happens when an item is below 1KB? Can multiple items fun within a single WCU?

# Reading
## RCU (Read Capacity Units)
- Represents one SCR or two ECR per second for an item up to 4KB in size
- ! # of KBs is rounded up to nearest 4KB (6.5KB → 8KB)
## Strongly Consistent Read
Guarantees you will read in correct data right after a write
- ! Set “ConsistentRead” parameter to True in API calls
- ^ Consumes 2x the RCUs as [[#^dcafd5|Eventually Consistent Read]]
- ^ Higher latency as it confirms the most recent commits and waits for **replication**

## Eventually Consistent Read

^dcafd5

Reading just after a write may result in seeing stale data due to replicated data not being immediately updated
- $ Consumes less RCUs (.5 RCUs per 4KB)

# Autoscaling
- Used to allow the database to dynamically change WCU and RCU provisions based on how much of the current usage compares to the provisioned usage
	- e.g. 100 provisioned and 50 utilized → 50% utilization
	  If your target utilization is 70%, the system would decrease your provisioned pool to close the gap between 50% and 70%
	- You set a min and max number of provisioned WCUs and RCUs to limit how far the autoscaling automatically modified the provisions
# Partitions
- Data within a DynamoDB database are stored across multiple storage units
- ! This is done through a hash function that then places the item within a partition that includes the range of hash values
- Lookup for which partition is O(1)
- DynamoDB partitions details are not shown to the user
## Data Modeling
### Primacy of Primary Keys

| Action              | Requirement      | Notes                         |
| ------------------- | ---------------- | ----------------------------- |
| Single-item actions | Full primary key |                               |
| Query               | Partition key    |                               |
| Scan                | Limited use      | Will scan the entire database |
### No Joins
- DynamoDB doesnt support joins as the partitioning makes combining data from different criteria very difficult
- Solutions:
	- Denormalization + duplication
# Throttling
- ! Hot Keys are partition keys that are being read too many times (e.g. popular item)
- Hot partitions are partitions where the specific set of values the partition is assigned to are being accessed more often than other partitions
- Very large items will utilize more RCU and WCU and thus may cause throttling
## Solutions
- Exponential backoff when exception is encountered (in the SDK)
- Distribute partition keys are much as possible
- If there is an RCU issue, DynamoDB Accelerator (DAX) can be used

# General Notes
- You can switch between the two modes every 24 hours
- Read Capacity Units (RCU) and Write Capacity Units (WCU)
- Burst capacity allows throughput to be temporarily exceeded
- When burst capacity is consumed you receive a ProvisionedThroughputExceededException
	- ! Advised to do an exponential backoff retry
- 

