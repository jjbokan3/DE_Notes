# Writing Data

| Command            | Usage                                                                                                      | Tips                                  |
| ------------------ | ---------------------------------------------------------------------------------------------------------- | ------------------------------------- |
| PutItem            | Creates a new item or fully replaces an old item if primary key matches                                    |                                       |
| UpdateItem         | Edits an existing item’s attribute or creates a new item if it doesn’t exist already                       | Can implement Atomic Counters         |
| Conditional Writes | Will write/update/delete an item if certain conditions are met; Will return an error if it doesn’t satisfy | Helps with concurrent access to items |

# Reading Data

| Command | Usage                                                               | Tips                                                                                                                                                      |
| ------- | ------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| GetItem | Read based on a primary key which can be of type HASH or HASH+RANGE | Eventually Consistent is on by default but Strongly Consistent can be specified; ProjectionExpression can be specified for particular attribute retrieval |
| Query   | More advanced item retrival                                         | [[#Query]]                                                                                                                                                |
## Query
### KeyConditionExpression
- Partition Key value which must use equality (=) comaprison
- Sort Key value which can utilize =, <, >, ≤, ≥, Between, or Begins with
	- ! This field is optional
### FilterExpression
- Additional filtering after the data is returned from the Query
- $ Can be based on non-key attributes
### ProjectionExpression
- Used to specify the attribute you want to retrieve
- $ Can reduce the amount of data retrieved

## Returns
- Retrieves either
	- Number of items specified in **Limit**
	- 1 MB of data
- ! Pagination can be used to pull more results
- $ Can query both tables and indexes (Local Secondary and Global Secondary)

# Scan Data
- ^ Scans the entire table and then data is filtered
- ^ Consumes a lot of RCU
- ! 1 MB limit so pagination can be utilized to pull more results
- ! Limit will impact how many rows are returned
- $! Parallel Scan can be used to improve performance considerably but at a huge cost to RCU
- [[#ProjectionExpression]] and [[#FilterExpression]] can be used with no impact to RCU

# Deleting Data

| Command     | Usage                                 | Tips                                     |
| ----------- | ------------------------------------- | ---------------------------------------- |
| DeleteItem  | Deletes an individual item in a table | Can perform a conditional                |
| DeleteTable | Deletes an entire table               | Much faster than DeleteItem on all items |
# Batch Operations
- $ Allows you to save in latency by reducing the number of API calls
- $! Completed in parallel for better efficiency
- When items in a batch fail, they are listed as UnprocessedItems and will need to be run again

| Command        | Usage                                              | Tips                                                                                                                                                                                                                  |
| -------------- | -------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| BatchWriteItem | Will write multiple items within a single call     | - Up to 25 PutItem or DeletItem per call<br>- Up to 16 MB of data written and up to 400KB of data per item<br>- Can’t update items<br>- UnprocessedItems are failed write operations (exponential backoff or add WCU) |
| BatchGetItem   | Will return multiple items from one or more tables | - Up to 100 items and up to 16MB of data<br>- Items retreived in parallel<br>- UnprocessedKeys are failed read operations (exponential backoff or add RCU)                                                            |
|                |                                                    |                                                                                                                                                                                                                       |
# PartiQL
- $! Allows you to select, insert, update, and delete data in DynamoDB using SQL
- ^ No joins as previously stated 
- Can be run from
	- AWS Management Console
	- NoSQL Workbench for DynamoDB
	- DynamoDB APIs
	- AWS CLI
	- AWS SDK

