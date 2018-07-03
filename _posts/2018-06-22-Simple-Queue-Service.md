---
  layout: post
  title: Simple Queue Service
  subtitle: 
  tags: [ sqs, messaging, polling ]
  categories: messaging
  author: Eshan Shafeeq
  header_img: 
---

Amazon SQS is a web service that gives you access to a message queue that can be used to store messages while waiting for a computer to process them. Amazon SQS is a distributed queue system that enables web service applications to quickly and reliably queue messages that one component in the application generates to be consumed by another component. A queue is a temporary repository for messages that are awaiting processing.

Using amazon SQS, you can decouple the components of an application so they run independently, with Amazon SQS easing message management between components. Any component of a distributed application can store messages in a fail-safe queue.

Messages can contain upto 256KB of text in any format. Any component can later retrieve the messages programmatically using the Amazon SQS API. The queue act as a buffer between the component producing and saving data, and the component receiving the data for processing. This means the queue resolves issues that arise if the producer is producing work faster than the consumer can process it, or if the producer or consumer are only intermittently connected to the network.

Amazon SQS ensures delivery of each message at least once, and supports multiple readers and writers interacting with the same queue. A single queue can be used simultaneously by many distributed application components, with no need for those components to coordinate with each other to share the queue.

Amazon SQS is engineered to always be available and deliver messages. One of the resulting tradeoffs is that SQS does not guarantee first in, first out delivery of messages. For many distributed applications, each message can stand on its own, and as long as all messages are delivered, the order is not important.

If your system requires that the order be preserved, you can place sequencing information in each message, so that you can reorder the messages when the queue returns them.

### Example
Suppose you have a number of images which needs to be encoded, In an amazon SQS worker queue, you can create an SQS message for each file specifying the command (jpeg-encode) and the location of the file in amazon s3. A pool of EC2 instances running the needed image processing software does the following:

1. Asynchonously pull the task messages from the queue. ( polling from the queue ).
2. Retrieves the named file.
3. Processes the conversion.
4. Writes the image back to S3
5. Writes the "task-complete" message to another queue.
6. Deletes the original task message.
7. Checks for more messages in the working queue.


> You can enable auto scaling depending on the size of the queue. More messages in the queue, more ec2 instances you spin up.

### Exam Tips
* Does not offer FIFO.
* 12 hours visibility timeout.
* Will deliver messages at least once, most of the time it does deliver your messages exactly once. Design your applications so that even if it did deliver the message more than once, it doesnt create errors.
* 256KB message sizes now available.
* Billed at 64KB chunks.
* 256 KB messages will be billed at 64 x 4.
* First 1 million amazon SQS requests are free.
* $0.50 per 1 million Amazon SQS Requests per month thereafter.
* A single request can have from 1 to 10 messages, up to a maximum total payload of 256KB.



