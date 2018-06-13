---
  layout: post
  title: S3 Cross Region Replication
  subtitle: 
  tags: [ crossregionreplication, s3, storage ]
  categories: storage
  author: Eshan Shafeeq
  header_img: 
---

### Instructions

* Create 2 buckets one in london, and sydney
* Enable Cross Region Replication on the london bucket
    * In order for Cross Region Replication to work, you need both buckets with versioning enabled.
    * You can enable CRR on just a prefix on a bucket.
    * Set the bucket storage class from standard to IA.
    * Hit save!
    * Existing objects will not be replicated into both the buckets, Only new objects get replicated into the other buckets
* If you want to copy your current items in bucket one to bucket two.
```shell
aws s3 cp --recursive s3://[bucket_1] s3://[bucket_2]
```
    * Items that have been copied over, by default has permission set to private.
    * If you delete an item from bucket 1, it sets a delete marker on bucket 1 and does the same on bucket 2.
    * If you delete the delete marker on bucket 1 it does not delete on bucket 2.
    * If you revert to an older version in bucket 1, you must do so in bucket 2, because the changes are not refelcted automatically in bucket 2.

### Exam Tips
* Versioning Must be enabled on both the source and destination buckets
* Region must be unique.
* Files in an existing must be replicated across regions manually, otherwise it does not get replicated automatically.
* You cannot replicate to multiple bucket or daisy chain it at this time.
* delete markers are replicated.
* deleting individual version or delete markers will not be replicated.
* Understanding what cross region replication is at a high level.
