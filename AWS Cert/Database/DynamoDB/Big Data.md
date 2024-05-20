# Best Uses Cases
- Mobile Apps
- Gaming
- Digital ad serving
- Live voting
- Audience integration for live events
- Sensor networks
- Log ingestion
- Access control for web based content
- Metadata storage for Amazon S3 objects
- E-commerce shopping carts
- Web session management

# Bad Use Cases (Anti Pattern)
- Applications already utilizing an RDS
- Joins and complex transactions
- Binary Large Object (BLOB) data -> Store data in S3 and metadata in DynamoDB
- Large data with low I/O rate -> S3 instead

