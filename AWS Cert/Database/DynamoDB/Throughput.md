*Controling table's capacity (read/write)*

# Provisioned Mode
Default mode that provides a set amount of read/writes per seconds
- $ Cheaper
- ^ Need to plan ahead of time
# On Demand Mode
Read/writes scale automatically with the workflow demands.
- $ No planning ahead of time needed
- $ Pay only for what you use
- ^ Much more expensive

# Writing
## WCU (Write Capacity Units)
- Represents one write per second for an item up to 1 KB in size
- ! If items are larger than 1 KB, they will use more WCU
- ! # of KBs is rounded up (2.2KB -> 3KB)

# Reading
## RCU (Read Capacity Units)
- Represents one SCR or two ECR per second for an item up to 4KB in size
## Strongly Consistent Read
Guarantees you will read in correct data right after a write
- ! Set “ConsistentRead” parameter to True in API calls
- ^ Consumes 2x RCUs as [[#^dcafd5|Eventually Consistent Read]]
- ^ Higher latency

## Eventually Consistent Read

^dcafd5

Reading just after a write may result in seeing stale data due to replicated data not being immediately updated
- $ Consumes less RCUs

# General Notes
- You can switch between the two modes every 24 hours
- Read Capacity Units (RCU) and Write Capacity Units (WCU)
- Burst capacity allows throughput to be temporarily exceeded
- When burst capacity is consumed you receive a ProvisionedThroughputExceededException
	- ! Advised to do an exponential backoff retry
- 

