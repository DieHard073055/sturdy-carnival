---
  layout: post
  title: S3 Enable Versioning
  subtitle: 
  tags: [ storage, s3, versioning ]
  categories: storage
  author: Eshan Shafeeq
  header_img: 
---


### Instructions
* Loggin to the aws console and head over to aws s3
* Create a new bucket, click next instead of create.
* Enable versioning and click next until bucket is created.
* Once versioning has been enabled for a bucket.
    * You cannot remove versioning from the bucket.
    * You can stop the bucket from creating more versions.
    * If you want to completely remove versioning from the bucket, create a new bucket, transfer everything to that bucket.
* If you deleted an object, you can restore that object as well. You will be able to restore it to any point in time.

### Tips
* Stores all versions of an object (including all writes and even if you object)
* Great Backup tool
* Once enabled, Versioning cannot be disabled, only suspended.
* Integrated with Life cycle rules.
* Versioning's MFA Delete capability, which uses multi-factor authentication, can be used to provide an additional layer of security. ( bucket level and object level )

