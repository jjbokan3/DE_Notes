# Data Formats
## Structured Data
- Easily queryable
- Rows and columns
- Consistent strucute
Examples:
- Database tables
- csv
- Excel

## Unstructured Data
Data that doesnt have a predefined strucutre
Examples:
- Text files
- Videos and images and audio
- Emails and word processing documents

## Semi Strucutred Data
Data that is not organized like strucutred data but has some level of structure (tags, hierachies)
Examples
- XML and JSON
- Email headers
- Log files

# Properties of Data
## Volume
- Amount or size of data that organization is dealing with
- GBs to PBs
- Chanllenges involve:
	- Storing
	- Processing
	- Analyzing high volumes of data

## Velocity
- Speed at which new data is collected, generated, processing
- **Real Time vs near Real Time** 
Examples:
- Sensor data
- Trading application

## Variety
- Different types, strucutre, and sources of data
- Data can be structured, semi strucutred or unstructured

# Warehouse vs Lake
## Warehouse
Centralized repo for analysis where data from multiple sources can be queried
- Complex queries
- ETL
- Star or Snowflake schema
- Optimized for read heavy operations 
Examples:
- Amazin Redshift
- Google Bigquery
- Microsoft Azure SQL Data Warhouse

## Data Lake
Storage repo that stores raw data in its native format including all three [[#Data Formats]] 
- Data is loaded as is with no preprocessing
- Supports batch, real-time, and stream processing
- Queried for data transformation or exploration purposes
Examples:
- Amazon S3
- Azure Data Lake Storage
- HDFS

### Data Lakehouse
Hybrid that combines ideals of both Lakes and warehouses
- Supports both strucutred and unstructured data
- Schema on write and schema on read
- Allows detailed analytics and machine learning tasks
- Delta Lake -> ACID transactions to big data
Examples:
- AWS Lake Formation (with S3 and Redshift Spectrum)
- Delta Lake
- Databricks Lakehouse Platform
- Azure Synapse Analytics

## Differences
### Schema
- Data Warehouse - schema on write (ETL)
- Data Lake - schema on read (ELT)
### Data Types
- Data Warehouse - Primarily structured data
- Data Lake - Both strucutred and unstructured data
### Agility
- Data Warhouse - Less agile due to predefined schema
- Data Lake - More agile since it accepts raw data

### Cost
- Data Warehouse - Typically more expensive because of optimzations for complex queries
- Data Lakes - Cost effective but costs rise with large amounts of data

## Choice
Data Warehouse
- Structured data sources
- Complex and fast queries
- Data integration from different sources is important
- BI and analytics
Data Lakes
- All [[#Data Formats]] included
- Scalable and cost effective
- Future needs for data are uncertain
- Advanced analytics, ML, data discovery
Companies usually use BOTH

# Data Mesh

> [!INFO] Definition
> Governance of data where individual teams own certain data products within a domain.
> The products have various use cases that can link the domains that the products sit in

- Also considered "Domain-based data management"
- Each domain is responsible for governance (there are central standards normally)

# ETL Pipelines

> [!Info] Definition
> Extract, Transform, Load
> Moving data from source systems into a data warehouse

## Extract
- retreive raw data from source systems (Databases, CRMs, flat files, APIs)
- Data integrity
- Batches? Real time? Near real time?

## Transform
Convert extracted data into format suitable for targe warehouse
- Data cleansing
- Data enrichment
- Format changes
- Aggregations or computations
- Encoding or decoding data
- Missing values

## Load
- Move transformed data into the warehouse or other repo
- Can be done in batches or in streaming
- Data integrity
## Managing ETL Pipelines
- AWS Glue
- Orchestration tools
	- EventBridge
	- Amazon MWAA
	- AWS Step Functions
	- Lambda
	- Glue Workflows

# Data Sources
## Database Connectivity
### JDBC
Java Database Connectivity
- Platform-**independent**
- Language-**dependent**
### ODBC
Object Database Connectivity
- Platform-**dependent** (drivers)
- Language-**indpendent**

## Others
- Raw logs
- API's
- Streams
## File Formats
### CSV
Tabular format where lines represent rows
When to use:
- Small to medium datasets
- Data interchange, allowing communication with most systems
- Human readable and editable
- Importing/Exporting from databases or spreadsheets

Systems:
- Databases (SQL-based)
- Excel
- Pandas
- R
- ETL Tools

### JSON
Represents structured or semi-structured data based on key-value pairs
When to use:
- Data interchange between web server and web client
- Configs and setting files
- Flexible schema or nested data structures
Systems:
- Web browsers
- JS
- Python
- Java
- RESTful APIs
- NoSQL databases

### Avro
Binary format that stores both the data and schema
When to use:
- Big data and real time processing
- When schema evolution (changes in data structure)
- Efficient serialization
Systems:
- Kafka
- Spark
- Apache Flink
- Hadoop

### Parquet
Columnar storage format optimized for analytics. Allows for efficient compression and encoding
When to use:
- Analyzing big datasets with analytics engines
- Reading specific columns instead of entire records is useful
- Storing data on distributed systems
Systems:
- Spark
- Hadoop
- Hive
- Impala
- Redshift Spectrum

# Modeling
## Data Lineage


> [!Info] Definition
> Visual representation that traces the flow and transformation of data through its lifecycle

Importance
- Helps in tracking errors
- Ensures compliance
- Provides clear understanding of how data is moved, transformed, and consumed

Examples:
- Use SplineAgent attached to Glue
- Dump lineage into Neptune via lambda

![[Pasted image 20240416203847.png]]
## Schema Evolution
Ability to adapt and change the schema of a dataset without disrupting the existing processes or systems
Importance:
- Ensures data meets changing business requirements
- Addition, removal, or modification of columns/fields in a dataset
- Backwards compatibility with older data records
Example:
- Glue Schema Registry
	- Schema discovery, compatibility, validation, registration

# Database Perfomance Optimization
## Indexing
Avoids full table scan to quickly access certain data
Enforces data uniqueness and integrity

## Partitioning
Reduce amount of data scanned
Helps with data lifecycle management
Enables parallel processing

## Compression
- Speed up data transfer, reduce storage & disk reads
- GZIP, LZOP, BZIP2, ZSTD (Redshift exmaples)
	- Various trafeoffs between compression and speed
- Columnar compression

## Data Skew
When partitioning is inbalanced in a distributed system
"The Celebrity Porblem"
- Even partitioning doesnt work if your traffic is uneven
Causes:
- Non uniform distribution of data
- Inadequate partitioning strategy
- Temporal skew
Addressing:
- Adaptive Partitioning
- Salting
- Repartitioning
- Sampling
- Custom Partitioning

# Data Validation & Profiling
Completeness
- Ensures all required data is present
- Missing Values, null counts, percentage of populated fields
- Missing data leads to inaccurate analyses
Consistency
- Ensures data values are consistent and dont contradict each other
- Cross field validation
- Inconsistency causes confusion
Accuracy
- Ensures data is correct and reliable
- Compare with trusted sources
- Can lead to false insights
Integrity
- Data maintains its correctness and consistency over its lifecycle
- Foreign key checks

