# When should I use Aurora (MySQL) Serverless as my Data Store?

In this article, we will cover the various attributes of Aurora Serverless that will help guide why you might choose Aurora Serverless for your data storage needs. This article assumes you are already familiar with data storage terms and have a good understanding of data storage concepts. It is recommended to have already a data model with read and write requirements available while reviewing the data store material.

| Database Type | Data Storage Temprature |
| ------------- | ------------- |
| Relational | Hot or Warm |

## Volume

| Max Record Size | Max Number of Records | Growth Capcity |
| ------------- | ------------- | ------------- |
| 65.535 KB | 64 tebibytes (TiB) | Linear |

## Velocity

| Max Read I/O | Max Write I/O |
| ------------- | ------------- |
| 500,000 SELECTs/sec | 200,000 UPDATEs/sec |

In Aurora Serverless, database capacity is measured in Aurora Capacity Units (ACUs). 1 ACU has approximately 2 GB of memory with corresponding CPU and networking, similar to what is used in Aurora Standard instances. You pay a flat rate per second of ACU usage, with a minimum of 5 minutes of usage each time the database is activated. As your database capacity is automatically scaled up or down, ACUs are added or removed. 

## Variety

Aurora is optimized for storing structured data.

### Data Model

Your high level Data Model should incorporate Write and Read requirements.

## Query

Aurora supports standard MySQL query syntax and has a limit of 64 secondary indexes.

## Data Lifecycle

None

## Scaling

Aurora Serverless can auto-scale from a minimum of 2 ACUs to a maximum of 256 ACUs. You can specify the minimum and maximum ACUs your database can consume.