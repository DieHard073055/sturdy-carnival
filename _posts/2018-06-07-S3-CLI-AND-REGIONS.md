---
  layout: post
  title: S3 CLI AND REGIONS
  subtitle: This will include all the good habits to have when access aws resources via aws cli
  tags: [ goodhabits, compute, s3, awscli, ec2, lab ]
  categories: compute
  author: Eshan Shafeeq
  header_img: 
---


### Instructions

1. Launch an EC2 instance with the default settings, and no roles attached to it.
    * t2.micro
    * Amazon linux AMI
    * default configuration settings
    * add to a security group which has HTTP, HTTPS and SSH from 0.0.0.0

2. Create 3 S3 buckets.
    * One in London
    * One in Northern Virginia
    * One in Sydney

3. Add some random objects to those buckets.
    * Should be unique

4. Create a role with `amazon s3 full access` and attach it to your EC2.

5. SSH into your ec2 instances, and you can copy those items from your buckets into your ec2 instance
```shell
aws s3 cp s3://[bucketname] ./
```
    * This works regardless of which region the bucket is in, before you would have to provide the --region flag with the region.

