---
  layout: post
  title: S3 Security and Encryption
  subtitle: 
  tags: [ s3, security, encryption, secure, administration, storage ]
  categories: storage
  author: Eshan Shafeeq
  header_img: 
---

### Security
* By default, all newly created buckets are **PRIVATE**.
* You can setup access control to your buckets using;
    * Bucket Policies - Permissions are applied to the entier bucket.
    * Access Control List - You can apply different permissions to different objects in the buckets.
* S3 Buckets can be configured to create access logs which log all the requests made to the S3 bucket. This can be done to another bucket.

### Encryption
* In transit ( When sending object to and from your PC )
    * SSL/TLS Encryption ( HTTPS )
* At Rest ( When the objects are either in your PC or in the Server )
    * Server Side Encryption
        * S3 Managed Keys - SSE-S3
        * AWS Key Management Service ( AWS KMS ) - Managed Keys - SSE-KMS
            * These keys provide an audit trail, lets you know who has been using the keys.
            * Who has been decrypting what and when was it done.
        * Server Side Encryption with Customer Provided Keys - SSE-C
    * Client Side Encryption ( You encrypt the files and then you upload them to S3 )

