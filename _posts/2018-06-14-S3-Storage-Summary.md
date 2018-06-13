---
  layout: post
  title: S3 Storage Summary
  subtitle: 
  tags: [ storage, s3, summary ]
  categories: storage
  author: Eshan Shafeeq
  header_img: 
---

### S3 - Exam Tips 
* S3 is an Object based storage, its a place where you upload and download files.
    * You cannot run an os, or run a database off of S3.
* Files can be of size 0 bytes all the way to 5TB.
* There is unlimited storage.
* Files are stored in Buckets.
* S3 is a universal namespace, all bucket names shall be unique globally.
* S3 bucket names are like `https://s3-[region].amazonaws.com/[bucketname]`
* Read after Write Consistency for PUTS of new objects.
* Eventual Consistencry for Overwrite PUTS and DELETES. ( takes some time to propergate )
* S3 Storage Classes / Tiers
    * Standard S3
        * reliability of 99.999999999%
        * availability of 99.99%
        * Immedietly available and frequently accessed
    * S3 Infrequent Access ( IA )
        * availablity of 99.99%
        * reliability of 99.999999999%
        * Immedietly available infrequently accessed.
        * Charged for retreval
    * S3 Reduced Redundency
        * reliability and availability of 99.99%
        * Used for reproducable content ( such as thumbnails etc ).
    * Glacier
        * Archived data, where you have to wait 3 - 5 hour waiting period.
* Core fundementals of S3
    * Key ( name )
    * Value ( data )
    * Version ID
    * Metadata ( data about data )
    * Access control lists
    * Object based stroage only ( flat files )
* S3 versioning
    * Stores all versions of an object ( including all writes and even if you delete an object )
    * Great backup tool
    * You pay for storage for all the versions of the object.
    * Once enabled versioning cannot be disabled, it can only be suspended.
    * Integrates with lifecycle rules.
    * Versionings MFA Delete capability, which uses multi-factor authentication, can be used to provide an additional layer of security.
    * Cross region replication requires versioning enabled on both the source bucket and destination bucket.
* Lifecycle Management
    * Can be used in conjunction with versioning.
    * Can be applied to current versions and previous versions.
    * Following actions can now be done.
        * Transition to infrequenct access after a minimum of 30 days since creation date ( files need to be minimum 128kb )
        * Archived to glacier storage class ( 30 days after IA, if relevant ).
        * Permenantly Delete Objects
* CloudFront
    * Edge Locations - This is the location where content will be cached.
    * Origin - This is the origin of all the files that the CDN will distribute. This can be either an S3 bucket, an EC2 instance, an Elastic Load balancer or Route53.
    *  Distribution - This is the name given to the CDN with a collections of Edge Locations.
        * Web Distribution - Typically used for websites
        * RTMP - Used for Media Streaming
    * Edge locations are not just readonly, you can write to them as well. ( Upload files to S3 ).
    * Object are cached for the life of the TTL ( time to live ) ( default ttl 24hours )
    * You can clear cached objects, but you will be charged.
* Securing your buckets.
    * By default, all newly created buckets are **PRIVATE**.
    * You can setup access control to your buckets using;
        * Bucket policies.
        * Access Control Lists.
    * S3 buckets can be configured to create access logs which logs all the access requests made to the bucke. These logs can be stored in another bucket.
* Encryption
    * In-transit Encryption
        * SSL/TLS (HTTPS)
    * In rest
        * Server Side Encryption
            * S3 Managed Keys SSE-S3
            * AWS Managed Keys SSE-KMS
                * Allows you to monitor who decrypted which file when. (Audit trail)
            * Customer provided Keys SSE-C
        * Client Side Encryption
            * Client uploads encrypted files.

* Storage Gateway
    * File Gateway - for flatfiles,  stored directly on S3.
    * Volume Gateway (ISCI) - block based storage
        * Stored Volumes - your on premises data is asynchronously backed up to S3.
        * Cached Volumes - frequently accessed data is cached on premises from S3.
    * Gateway VIrtual Taped Library (VTL)
        * Used for backing up your data, from application like Netbackup, Backup Exec, Veam etc.

* Snowball
    * Snowball - Pure storage 50TB to 80TB
    * Snowball Edge - Both Compute and Storage Capabilities
    * Snowmobile - 100PB worth of storage
    * Understand what snowball is
    * Understand what Import/Export is
    * Snowball can import / Export to S3

* S3 Transfer Acceleration
    * You can speed up S3 transfer speeds using CloudFront Edge locations, so you can upload files to s3 faster. Extra costs will apply. Greatest Impact on people who are further away geographically.

* S3 static websites.
    * You can S3 to host static websites.
    * Serverless
    * Very Cheap, scales automatically.
    * Static only, cannot host dynamic sites.
* CORS
    * Cross origin resource sharing
    * Needed to enable cors on the resources bucket and state the URL for the origin that will be calling the bucket.
    * Remeber to use the S3 website url and not the bucket URL, website url has the word website on it.

* When you do a PUT object on S3 you will get a HTTP 200 success code.
* You can load files much faster by enabling multipart upload.
* Read the S3 FAQ!

