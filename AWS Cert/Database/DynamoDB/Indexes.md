*Gives you an alternative sort key (same as the Partition Key of the base table*

## Local Secondary Index (LSI)
- ! Is basically a way of querying a specific attribute/field more efficiently
- $ Up to 5 LSIs per table
- ^ Must be defined at table creation time

## Global Secondary Index (GSI)
- 
## Attribute Projections
*Allows you to easily include attributes to create indexes*

|     |     |
| --- | --- |
|     |     |
## Info
- $ Can increase the query performance of both the original key as well as other attributes in the table
- ^ Will increase the storage cost as the index (like that of an RD) will need to be stored as well
- ^ Will increase the write cost as the index will have to be updated as well when data is created or updated
- ! As indexes are stored at the partition level, they will count towards the 10GB limit for each partition
- 