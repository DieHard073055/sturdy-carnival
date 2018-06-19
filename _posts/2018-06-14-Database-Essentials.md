---
  layout: post
  title: Database Essentials
  subtitle: 
  tags: [ database, rds ]
  categories: database
  author: Eshan Shafeeq
  header_img: 
---

### What is a relational database ?
Relational databases are what most of us are all used to. They have been around since 70's. Very similar to the traditional spread sheet.

* Database
* Tables
* Row
* Fields ( Columns )

Relational Database Types

* SQL Server
* Oracle
* MySQL Server
* PostgresSQL
* Aurora
* MariaDB

> Read the FAQ for RDS and DynamoDB

Non Relational Databases
* Database
    * Collection        = Table
    * Document          = Row
    * Key Value Pairs   = Field

### What is Database Warehousing ?
Used for business intelligence. Tools like Cognos, Jaspersoft, SQL Server Reporting Services, Oracle Hyperion, SAP NetWeaver. Used to pull in very large and complex data sets. Usually used by management to do queries on data (such as current performance vs target etc).

### OLTP VS OLAP
Online transaction processing verses online analytics processing are 2 different things interms of the types of queries you run on a database.

OLTP example : Pulls up a row of data such as Name, Date, Address to Deliver to, Delivery Status etc.
OLAP example : Figure out the net profit for a digital radio product.
    * Sum of radios sold in EMEA
    * Sum of radios sold in Pacific
    * Unit cost of radio in rach region
    * Sales price of each radio
    * Sales price - unit cost

Data Warehousing databases use different type of architechture both from a database perspective and insfrastructure layer.

### Elasticache
ElasticCache is a web service that makes it easy to deploy, operate, and such an in-memory cache in the cloud.The service improves the performance of web applications by allowing you to retrieve information from fast, amanged, in-memory caches, instead of relying entirely on slower disk-based databases. ElasticCache supports two open-source in-memory caching engines:
* Memcached
* Redis

### Database Migration Service
Annouced at re:invent 2015. Allows you to migrate your production database to AWS. Once the migration has started, AWS manages all the complexities of the migration process like data type transformation, compression, and parallel transfer ( for faster data transfer ) while ensuring that data changes to the source data that occur during the migration process are automatically relicated to the target.
AWS schema conversion tool automatically converts the source database schema and a majority of the custom code, including views, stored procedures, and functions, to a format compatible with the target database.

### AWS Database Types - Summary

* RDS - OLTP
    * SQL
    * MySQL
    * PostgresSQL
    * Oracle
    * Aurora
    * MariaDB

* DynamoDB - No SQL
* RedShift - OLAP
* Elasticache - In Memory Caching
    * Memcached
    * Redis
* DMS - Database Migration Service

