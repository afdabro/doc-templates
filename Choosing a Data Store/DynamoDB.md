# When should I use DynamoDB as my Data Store?

In this article, we will cover the various attributes of DynamoDB that will help guide why you might choose DynamoDB for your data storage needs. This article assumes you are already familiar with data storage terms and have a good understanding of data storage concepts. It is recommended to have already a data model with read and write requirements available while reviewing the data store material.

| Database Type | Data Storage Temprature |
| ------------- | ------------- |
| NoSQL Document Store | Hot or Warm |

## Volume

| Max Record Size | Max Number of Records | Growth Capcity |
| ------------- | ------------- | ------------- |
| 400 KB | No limit | Linear |

## Velocity

| Max Read I/O | Max Write I/O |
| ------------- | ------------- |
| 40,000 read capacity units | 40,000 write capacity units |


Notes
* One read capacity unit = one strongly consistent read per second, or two eventually consistent reads per second, for items up to 4 KB in size.

* One write capacity unit = one write per second, for items up to 1 KB in size.

## Variety

DynamoDB is optimized for storing Semi-structured data.

### Data Model

Your high level Data Model should incorporate Write and Read requirements. DynamoDB has support for querying but is limited by the number of indexes. This may limit business use cases for querying by multiple field combinations.

## Query

DynamoDB provides querying with the following limitations:

* Table must have a composite primary key (partition key and sort key).
* Maximum of 5 global secondary indexes per table.
* Maximum of 5 local secondary indexes per table.
* You must specify an equality condition for the partition key
* You can optionally provide another condition for the sort key.
* The result set from a Query is limited to 1 MB per call.

## Data Lifecycle

DynamoDB supports Time to Live (TTL) which allows you to define when items in a table expire so that they can be automatically deleted from the database.

## Scaling

DynamoDB supports auto-scaling throughput with the following limitation:

Currently, Auto Scaling does not scale down your provisioned capacity if your table’s consumed capacity becomes zero. As a workaround, you can send requests to the table until Auto Scaling scales down to the minimum capacity, or change the policy to reduce the maximum provisioned capacity to be the same as the minimum provisioned capacity.

## Cost Analysis for Read Heavy Applications

### Cost Assumptions

* Dataset volume is variable but will increase at a fixed rate. Cost for the data store volume will be projected for 500GB, 1TB, and 3TB.
* Record size is fixed at 4KB.
* Data will only be transferred from/to DynamoDB through an AWS service (ie. AWS Glue, AWS Lambda, AWS ECS).
* Read to Write ratio is fixed at 4:1.
* Read is Strongly Consistent
* No reserved capcity will be purchased.

### Cost Performance

Dataset volume of 500GB

| Reads Per Second | Writes Per Second | Monthly Bill |
| ------------- | ------------- | ------------- |
| 5,000 | 1,250 | $3,258.58 |
| 10,000 | 2,500 | $6,398.86 |
| 20,000 | 5,000 | $12633.62 |
| 30,000 | 7,500 | $18,742.89 |
| 40,000 | 10,000 | $24,852.16 |

Dataset volume of 1TB

| Reads Per Second | Writes Per Second | Monthly Bill |
| ------------- | ------------- | ------------- |
| 5,000 | 1,250 | $3,406.19 |
| 10,000 | 2,500 | $6,546.47 |
| 20,000 | 5,000 | $12777.20 |
| 30,000 | 7,500 | $18,886.47 |
| 40,000 | 10,000 | $24,995.74 |


Dataset volume of 3TB

| Reads Per Second | Writes Per Second | Monthly Bill |
| ------------- | ------------- | ------------- |
| 5,000 | 1,250 | $3,983.14 |
| 10,000 | 2,500 | $7,123.42 |
| 20,000 | 5,000 | $13,338.42 |
| 30,000 | 7,500 | $19,447.69 |
| 40,000 | 10,000 | $25,556.96 |