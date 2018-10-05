---
  layout: post
  title: DynamoDB Provisioned Throughput Calculations
  subtitle: 
  tags: [ dynamodb, database, cost, throughput, calculations ]
  categories: database
  author: Eshan Shafeeq
  header_img: 
---


### Provisioned Throughput
* Unit of Read provisioned throughput
    * All reads are rounded up to increments of 4KB
    * Eventually Consistent Reads (default) consist of 2 reads per second.
    * Strongly Consistent Reads consist of 1 read per second.
* Unit of Write provisioned throughput.
    * All writes are 1 KB
    * All writes consist of 1 write per second

### The magic formula
* **Question** - you have an application that requires to read 10 items of 1KB per second using eventual consistency. What should you set the read throughput to?

> **(Size of Read rounded to nearest 4KB chunk / 4KB) x no of items = read throughput**
> **Divide by 2 if eventually consistent.**

    * First we calculate how many read units per item we need.

    * 1KB rounded to the nearest 4KB increment = 4KB
    * 4KB / 4KB = 1 read unit per item.

    * 1 x 10 read items = 10
    * Using eventual consistency we get 10 / 2 = 5
    * 5 units of read throughput

---


* **You have an application that requires to read 10 items of 6 KB per second using eventual consistency. What should you set the read throughput to?**
    * 6 KB rounded to the nearest 4KB increment = 8KB
    * 8KB / 4KB = 2 read unit per item
    * 2 x 10 read items = 20 
    * Using eventual consistency we get 20 / 2 = 10
    * 10 units of read throughput

---

* **You have an application that requires to read 5 items of 10KB per second using eventual consistency. What should you set the read throughput to?**
    * 10KB rounded to the nearest 4KB increment = 12KB
    * 12KB / 4KB = 3 read units per item
    * 3 x 5 read items = 15
    * using eventual consistency we get 15 / 2 = 7.5 (8) <- since read throughput can only be integer.
    * 8 units of read throughput.

---

* **You have an application that requires to read 5 items of 10KB per second using ***strong consistency***. What should you set the read throughput to?**
    * 10KB rounded to the nearest 4KB increment = 12KB
    * 12KB / 4KB = 3 read units per item
    * 3 x 5 read items = 15
    * Since we are using strong consistency 15 x 1
    * 15 units of read throughput

---

* **You have an application that requires to write 5 items, with each item being 10KB in size. What should the write throughput be set to?**
    * 10 KB rounded to the nearest 1KB = 10KB
    * 10 KB / 1 KB = 10 write units per item
    * 10 x 5 write items = 50
    * 50 units of write throughput

---

* **You have an application that requires to write 12 items, with each item being 100KB in size. What should the write throughput be set to?**
    * 100 KB rounded to the nearest 1KB = 100KB
    * 100 KB / 1 KB = 100 write units per item
    * 100 x 12 write items = 1200
    * 1200 units of write throughput

---

### Error Codes

* 400 HTTP Status Code **ProvisionedThroughputExceededException**
    * You have exceeded the maximum allowed provisioned throughput for a table or for one or global secondary indexes.


