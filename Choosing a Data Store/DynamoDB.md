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