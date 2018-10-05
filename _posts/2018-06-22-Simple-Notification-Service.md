---
  layout: post
  title: Simple Notification Service
  subtitle: 
  tags: [ messaging, notification, sns ]
  categories: messaging
  author: Eshan Shafeeq
  header_img: 
---

* Web service that makes it easy to setup, operate, and send notifications from the cloud.
* Provides developers with a highly scaleable, flexible and cost effective capability to publish messages from an application and immedietely deliver them to the subscribers.
* Follows the "pub-sub" paradigm - using a "push" mechanism. *no need for polling*.
* Pay as you go pricing.
* Email & SMS
* Push notifications to Apple, Google, FireOS, and Windows Devices, as well as Android Devices with Baidu Cloud Push.
* SQS and any HTTP endpoint.
* Stored in multiple availability zones. - prevents messages being lost.
* Allows you to group multiple recipients using topics.
* One topic can support deliveries to multiple endpoints ( Will be formatted Appropriately )
    * iOS
    * Android
    * SMS

### Benefits
* Instantaneous, Pushbased Delivery
* Simple API's and easy integration with applications.
* Flexible message delivery over multiple transport protocols.
* Inexpensive, pay-as-you-go model with no up-front costs.
* Web-based AWS Management Console offers the simplicity of a point-and-click interface.


### SNS vs SQS
* Both messaging services in AWS
* SNS - Push
* SQS - Pull ( Polls )

### Pricing
* $0.50 per 1 million SNS Requests
* $0.06 per 100,000 Notification Deliveries over HTTP
* $0.75 per 100 Notification deliveries over SMS
* $2.00 per 100,000 Notification deliveries over Email
*Number of requests + delivery mechanism*

> SNS dataype = JSON
