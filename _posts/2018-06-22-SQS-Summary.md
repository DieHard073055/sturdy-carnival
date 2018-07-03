---
  layout: post
  title: SQS Summary
  subtitle: 
  tags: [ summary, sqs, examtips ]
  categories: messaging
  author: Eshan Shafeeq
  header_img: 
---

* SQS messages can be delivered multiple times and in any order.
* Default visibility is 30 seconds.
* Maximum timeout is 12 hours.
* If you wish to extend the message visibility since the timeout is not enough to fully process and delete the message, you can use **Change Message Visibility** action to specify a new timeout value. Amazon SQS restarts the timeout period using the new value.
* SQS long polling dosent return a response until a message arrives in the queue, or the long poll times out. SQS long polling makes it easy and inexpensive to retrieve messages from your SQS queue as soon as they are available. *Maximum long poll timeout = 20 seconds*

##### Example Question
Polling in a tight loops is burning CPU cycles and costing the company money. How could you fix this?
**Enable long polling**

### Fanning out SQS
* Create an SNS topic in SNS.
* Create and subscribe multiple SQS queues to the SNS topic.
When ever a message is sent to the SNS topic, the message will be fanned out to the SQS queues. SNS will deliver the message to all the SQS queues that are subsribed to the topic.


