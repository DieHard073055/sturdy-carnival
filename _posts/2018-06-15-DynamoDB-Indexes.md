---
  layout: post
  title: DynamoDB Indexes
  subtitle: 
  tags: [ indexes, primarykeys, streams, dynamodb, nosql ]
  categories: database
  author: Eshan Shafeeq
  header_img: 
---

### Primary Key
Two types of primary keys available.
* **Single Attribute (unique ID)**
    * Partition Key (Hash Key) composed of one attribute.
* **Composite (unique ID and another attribute eg: DateRange)**
    * Partition Key & Sort Key ( Hash & Range ) composed of two attributes.

### Partition Key
* DynamoDB uses the partition keys value as input to an internal hash function. The output from the hash function determines the partition ( The physical location where the data will be stored. )
* No two items can have the same partition key.


### Partition Key & Sort Key
* DynamoDB uses the partition keys value as input to the internal hash function. The output determines the physical location just like the previous definition.
* Two items can have the same partition key, but the sort key must be different.
* All items with the same partition key will be stored together in sorted order by the sort key.

### Local Secondary Index
* Has the partition key, different sort key.
* Can **only be created when you create the table.** They cannot be removed / modified later either.

### Global Secondary Index
* Has a different partition key and a different sort key.
* Can be created when your creating the table, and it can be created or added later as well.

### DynamoDB Streams
Used to capture any kind of modification to the DynamoDB tables.
    * If a new item is added to the table, the stream captures an image of the entire item. including all of its attributes.
    * If an item is updated, stream captures the "before" and "after" image of any attributes that were modified in the item.
    * If an item is deleted from the table, the stream captures an image of the entire item before it was deleted.
    * If a new user signed up to your website, it creates a new entry in the user table, this will create a stream if you have streams enabled in your dynamo table. You can use the stream to **trigger** lambdas to update a dynamodb table in another region or send a welcome message to the user.

> You can export data to csv

> You can also enable cloudwatch to trigger alarms for different different metrics.

> You can have upto 5 local secondry indexes (LSI) and 5 global secondary indexes (GSI).



