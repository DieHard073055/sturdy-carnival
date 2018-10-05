---
  layout: post
  title: Simple Workflow Service
  subtitle: 
  tags: [ workflow, taskmanager ]
  categories: workflow
  author: Eshan Shafeeq
  header_img: 
---

Amazon Simple Workflow Service (Amazon SWF) is a web service that makes it easy to coordinate work across distributed application components. Amazon SWF enables applications for a range of use cases, including media processing, web application back-ends, business process workflows, and analytics pipelines, to be designed as a coordination of tasks.

Tasks represent invocations of various processing steps in an application which can be performed by executable code, web service calls, human actions, and scripts.

* Worker are programs that interact with amazon SWF to get tasks.
    * Process received tasks and return results.

* A decider is a program that controls the coordination of tasks, ie: their ordering, concurrency, and scheduling according to the application logic.

The workers can run on EC2 instances or on machines behind firewalls. Amazon SWF brokers the interactions between workers and deciders. Allows deciders to get consistent views into the progress of tasks and to initiate new tasks in an ongoing manner.

At the same Amazon SWF stores tasks, assigns them to workers when are ready, and monitors their progress. **It ensures that a task is assigned only once and is never duplicated.** Since Amazon SWF maintains the applications state durably, workers and deciders dont have to keep track of execution state. They can run independently, and scale quickly.

All your SWF activities are all scoped into a domain. Domains Isolate a set of types, execution, and tasks list from others within the same account.
*You can register a domain by using the AWS Management Console or by using the RegisterDomain action in the Amazon SWF API.*

> Parameters are defined in JSON

* **Maximum Workflow can be 1 year and the value is measured in seconds**

### SWF vs SQS
* Amazon SWF presents a task-oriented API, whereas Amazon SQS offers a message-oriented API.
* SWF ensures task is executed only once, where as SQS you have to handle duplicated messages.
* SWF keeps track of all the tasks and events in an application, whereas SQS you have to keep track of all the tasks and events.


