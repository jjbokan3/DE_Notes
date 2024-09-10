# Large Objects Pattern
*Allows you to store large objects within S3 while storing its location and other metadata in DynamoDB*
- $ ID will uniquely differentiate the images
- ! Will likely contain the S3 image URL as the value

# Indexing S3 Objects Metadata
*Allows you to index the data that is placed in an S3 bucket*
- $ Allows you to easily query S3 since you have the metadata associated with the objects placed

## Use Cases
- Search by date
- Total storage used by a customer
- List of all objects with certain attributes
- Find all objects uploaded within a date range