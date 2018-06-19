---
  layout: post
  title: DynamoDB Introduction
  subtitle: 
  tags: [ introduction, dynamodb, nosql, database ]
  categories: database
  author: Eshan Shafeeq
  header_img: 
---

### DynamoDB 101
Amazon DynamoDB is a fast and flexible NoSQL database service for all applications that need consistent, single-digit millisecond latency at any scale. It is a fully managed database and supports both document and key-value data models. Its flexible data model and reliable performance make it a great fit for mobile, web, gaming, ad-tech, IoT, and many other applications.

### Quick Facts about DynamoDB ?
* Stored on SSD Storage
* Spread Across 3 geographically distinct data centres.
* Eventual Consistent Reads (Defaults)
    * Consistency across all copies of data is usually reached within a second. Repeating a read after a short time should return the updated data. (Best Read Performance)
* Strongly Consistent Reads
    * A strongly consistent read returns a result that reflects all writes that recieved a successful response prior to the read.

### The Basics
* Tables
* Items ( Think a row of data in table )
* Attributes ( Think a column of data in a table )


> DynamoDB can have 35 levels of nesting currently.

### Pricing
* Provisioned Throughput Capacity
    * Write throughput $0.0065 per hour for every 10 units
    * Read throughput $0.0065 per hour for every 50 units

* First 25 GB stored per month is free.
* Storage costs of $0.25 per month there after.

Lets assume that your application needs to perform 1 million writes and 1 million reads per day, while storing 28GB of data. First, you need to calculate how many writes and reads per second you need. 1 million evenly spread writes per day is equivalent to 1,000,000 ( writes ) / 24 ( hours ) / 60 ( minutes ) / 60 ( seconds ) = 11.6 writes per second. A DynamoDB write capacity unit can handle 1 write per second, so you need 12 write capacity units. For write throughput you are charged $0.0065 for every 10 units.
So ($0.0065/10) * 12 * 24 = $0.1872 per day.

Similarly, to handle 1 million strongly consistent reads per day, you need 12 Read Capacity Units. For read throughput you are charged $0.0065 for every 50 units.
So ( $0.0065/50 ) * 12 * 24 = $0.0374 per day.

Storage costs is 0.25 per GB per month. Lets assume our database is 28GB. We get the first 25GB for free so we only pay for 3GB of storage which is $0.75 per month.

Total Cost = $0.1872 per day + $0.0374 per day Plus Storage of 0.75 per month
( 30 x ( $0.1872 + $0.0374 )) $0.75 = $7.488

With Free Tier You Get
25 Read Capacity Units
25 Write Capacity Units

### Easiest Way to Learn DynamoDB
* Play with DynamoDB

