---
  layout: post
  title: Elastic Beanstalk
  subtitle: 
  tags: [ loadbalancers, elastic, elasticbeanstalk, scale, webapps ]
  categories: loadbalancer
  author: Eshan Shafeeq
  header_img: 
---

* Deploy, monitor and scale applications quickly.
* Provides developers or end users with the ability to provision application infrastructure in an almost transparent manner.
* Gui for AWS
* Highly abstract focus towards infrastructure, focusing on components and performance - not configuration and specifications.
* Significantly simplify infrastructure management, allowing applications to be deployed into infrastructure environments easily.
* Primarily aimed at beginners.

### Key Architecture Components
* Applications are high level structure in beanstalk.
* Either your entier application, is one EB application.
* Each logical component of your application can be an EB application or a EB environment within an application.
* Applications can have multiple environments ( Prod, Staging, Dev, V1, V2, V1.1 or functional type [ backend, frontend] )
* Environments are either single instances or scalable.
* Environments are either web server environments or worker environments.
* Application versions are unique packages which represent versions of apps.
* An application is uploaded to Elastic beanstalk as a application bundle - .zip
* Each 'application' can have many different versions 1:M relationship.
* Application versions can be deployed to environments within an Application.

### Key configurations options
* PHP
* .NET
* Java
* Ruby
* Nodejs
* Python
* Go
* Docker

> You can do both application level updates, as well as configuration level updates. These can be rolling updates, all at once, one instance at a time, also do them by a percentage.

Elastic Beanstalk is a free service. But the services you provision from elastic beanstalk, the pricing depends on what you provision.

### Exam Tips
* You can have multiple versions of your application.
* You appplications can be split into tiers ( Web Tier / Application Tier / Database Tier ).
* You can update your application.
* You can update the configuration.
* Updates can be 1 instance at a time, a % of instances or an immutable update.
* You pay for the resources that you use, but elastic beanstalk is free.
* If elastic beanstalk creates your RDS database then it will delete it when you delete your application. If not then the RDS instance stays.
* Languages supported
    * Apache Tomcat for Java applications
    * Apache HTTP Server for PHP applications
    * Apacahe HTTP Server for Python applications
    * Nginx or Apache HTTP Server for Nodejs applications
    * Passenger or Puma for Ruby applications
    * Microsoft IIS, 7.5, 8.0, and 8.5 for .NET applications.
    * Java SE
    * Docker
    * Go

