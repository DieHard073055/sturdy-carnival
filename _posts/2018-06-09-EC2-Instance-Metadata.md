---
  layout: post
  title: EC2 Instance Metadata
  subtitle: How to access Instance metadata from an instance
  tags: [ ec2, metadata, compute, lab ] 
  categories: compute
  author: Eshan Shafeeq
  header_img: 
---

### Pre-requisite
Have an ec2 instance ready when you wanna start this lab.


### Instructions
In order to see a list of all the metadata for the ec2 instance you're on.
```shell
curl http://169.254.169.254/latest/meta-data
```
That should list out all the options available for you. For you to obtain the IPV4 public address for the ec2 instance.
```shell
curl http://169.254.169.254/latest/public-ipv4
```
That should give you the public ipv4.

You can use the same concept with any programming language to get the ec2 instance metadata.
