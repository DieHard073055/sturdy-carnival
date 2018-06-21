---
  layout: post
  title: DynamoDB - Other Key Facts
  subtitle: 
  tags: [ dynamodb, database, keyfacts ]
  categories: database
  author: Eshan Shafeeq
  header_img: 
---


#### Conditional Writes
Example Scenario

if two clients were to update a piece of data at the same time, the updates may happen at 2 different facilities, and may create unexpected outcome. In order to prevent this use, conditional writes. Lets say you want to update a price of an item, but you only want to update if its $6. So the first user do UpdateItem if Price is $6 to $15. The Price will change, the second user will also try and do a UpdateItem if Price is $6, but this time the price is 15 and the operation will fail.

> These conditional writes are idempotent. This means that you can send the same conditional write request multiple times, but will have no further effect on the item after the first successful update.

* DynamoDB support atomic counters, where you use the UpdateItem operation to increment or decrement the value of an existing attribute without interfering with other write requests. (All write requests are applied in the order in which they were recieved). For example, a web application might want to maintain a counter per visitor to their site. In this case, the application would need to increment this counter regardless of its current value.

* Atomic counter updates are not idempotent. This means the counter will increment each time you call UpdateItem. If you suspect that a previous request was unsuccessful, your application could retry the UpdateItem operation; however this would risk updating the counter twice. This might be acceptable for a web site counter, because you can tolerate with slightly over-or under-counting the visitors. However in a banking application, it would be safer to use a conditional update rather than an atomic counter.

**In the exam you will be asked if you should use the atomic counter or the conditional update, it depends if the data is critical, example voting or banking you would use conditional writes. Where as for website visitor counters you would use atomic counters.**

If your application needs to read multiple items, you can use the BatchGetItem API. A single ***BatchGetItem*** request can retrieve up to 1 MB of data, which can contain as many as 100 items. In addition, a single BatchGetItem request can retrieve items from multiple tables.


