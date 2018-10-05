---
  layout: post
  title: DynamoDB Summary
  subtitle: 
  tags: [ summary, dynamodb, database ]
  categories: database
  author: Eshan Shafeeq
  header_img: 
---

### What is dynamoDB
Fast and flexible NOSQL database service for all application that need consistent, single digit millisecond latency at any scale. It is a fully managed database and supports both document and key-value data models. Its flexible data model and reliable performance make it a great fit for mobile, web, gaming, ad-tech, IoT and many other applications.

### Quick Facts
* Stored on SSD Storage.
* Spread Across 3 geographically distinct data centres.
* Eventaul Consistent Reads (Default)
    * Consistency across all copies of data is usually reached within a second. Repeating a read after a short time should return the updated data. (Best read performance).

* Strong Consistent Reads
    * A strongly consistent read returns a result that reflects all writes that received a successful response prior to the read.

### Basics
    * Tables
    * Items ( Data in table )
    * Attributes ( Column names in a table )

### Primary Keys
**Two types of primary keys available**

Single Attribute (Unique ID)
* Partition Key (Hash key) composed of one attribute.

Composite (Think unique ID and a date range)
* Partition Key & Sort Key (Hash & Range) composed of two attributes.

* **Partition Key**
    * DynamoDB uses the partition key's value as input to an internal hash function. The output from the hash function determines the partition ( this is simply the physical location in which the data is stored).
    * No two items in a table can have the same partition key value!
* **Partition Key and Sort Key**
    * DynamoDB uses the partition key's value as an input to an internal hash function. The output from the hash function determines the partition ( this is simply the physical location in which the data is stored).
    * Two items can have the same parition key, but they **must have a different sort key.**
    * All items with the same partition key will be stored together but ordered using the sort key value.

### Indexes

**Local Secondary Index**
* Has the SAME parition key, different sort key.
* Can ONLY be created when creating a table. They cannot be removed or modified later.

**Global Secondary Index**
* Has a DIFFERENT partition key and DIFFERENT sort key.
* Can be created at table creation or added LATER.

### DynamoDB Streams
**Used to capture any kind of modification to the DynamoDB tables.**
* If a new item is added to the table, the stream captures an image of the entire item, including all of its attributes.
* If an item is updated, the stream captures the "before" and "after" image of any attributes that were modified in the item.
* If an item is deleted from the table, the stream captures an image of the entire item before it was deleted.

### Query & Scans
* A Query operation finds items in a table using only primary key attribute values. You must provide a partition key attribute name and a distint value to search for.
* A Scan operation examines every item in the table. By default,  a Scan returns all of the data attributes for every item; however you can use the **ProjectionExpression** parameter so that the Scan only returns some of the attributes, rather than all of them.
* Try to use a Query operation rather than a Scan operation as it is more efficient.

### DynamoDB Provisioned Throughput Calculation
* Read 13 items of 17 KB per second (using eventual consistency)
    1. 17KB to the nearest 4KB = 20
    2. 20KB / 4KB = 5 read units per item
    3. 5 x 13 read items per second = 65
    4. 65 / 2 for eventual consistency = 32.5 (33)
    5. 33 units of read throughput

* Write 94 items of 3KB per second
    1. 3KB to the nearest 1KB = 3
    2. 3KB/1KB = 3 write units per item
    3. 3 x 94 write items per second = 282
    4. 282 / 1 
    5. 282 units of write throughput capacity

* Error code
    * **400 HTTP ProvisionedThroughputExceededException** - You have exceeded your maximum allowed provisioned throughput for a table or for one or more global secondary indexes.
 
### Steps taken to authenticate with Web Identity Provider
1. User authenticates with Web identity Provider
2. They are passed a Token by their ID Provider
3. Your code calls **AssumeRoleWithWebIdentity** API and provides the providers token and specifies the ARN for the IAM Role.
4. App can now access DynamoDB from between 15 minutes to 1 hour (default 1 hour).


### Conditional Write
If a price equals **X** then update the price to **Y**. If the price is not equal to **X** operation fails. This is an **Idempotent** operation.

### Atomic Counters
Increment or Decrement a value on an existing attirbute, regardless of its value. This is not an Idempotent operation. May over-count or under-count.

* Use conditional writes for critical stuff, atomic counters for non critical stuff.

### Batch Operations
* **BatchGetItem** can contain upto 1MB of data and upto 100 items
* Can retrieve items from multiple tables.

***READ THE FAQ OF DYNAMODB***



