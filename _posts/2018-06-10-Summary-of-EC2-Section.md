---
  layout: post
  title: Summary of EC2 Section
  subtitle: Wrapping what we have covered on the EC2 section of the course
  tags: [ summary, wrappingup, ec2, compute, tips ]
  categories: compute
  author: Eshan Shafeeq
  header_img: 
---

* **Fundemental Topic**
* Remember to read the [EC2 FAQ](https://aws.amazon.com/ec2/faqs/) before going for the exam.

### Exam Tips
* Know the difference between the pricing models of EC2.
    * On Demand
    * Spot
    * Reserved
    * Dedicated Hosts

* Remember for Spot Instances
    * If you terminate the instance, you pay for the hour.
    * If aws terminates the spot instance, you get the hour it was terminated in for free.

* EC2 Instance Types.
    * Remember DRMCGIFTPX
    * D - Dense Storage
    * R - Memory Optimized
    * M - General Purpose ( Production )
    * C - Compute Optimized
    * G - Graphics Intensive
    * I - Storage Optimized
    * F - Field Programmable Gate arrays
    * T - Low Cost General Purpose
    * P - Graphics / General Purpose
    * X - Memory Optimized ( eXtreme Memory Optimized )

* EBS Consists of
    * SSD - General Purpose - GP2 - ( Up to 10,000 IOPS ).
    * SSD - Provisioned IOPS - IO1 - ( More than 10,000 IOPS ).
    * HDD - Throughput optimized - ST1 - Frequently accessed workloads.
    * HDD - Cold - SC1 - less frequently accessed data.
    * HDD - Magnetic - Standard - Cheap, infrequently accessed storage.
* You cannot mount 1 EBS Volume to multiple EC2 instances, instead use EFS.
* Termination Protection is turned off by default, You must turn on termination protection if you would like that safety.
* On an EBS backed storage, the default action on instance termination is deleting the EBS volume.
* Root Volumes cannot be encrypted by default unless you use a thirdparty tool to encrypt the root volume. (eg: Bitlocker )
* Additional Volumes can be encrypted.

* Volumes VS Snapshots
    * Volumes exists on EBS
        * Virtual Harddisks
    * Snapshots exists on S3
    * You can take snapshots of a volume, this will store that volume on S3.
    * Snapshots are point in time copies of that volume.
    * Snapshots are incremental, this means that only the blocks that have changed since your last snapshots are moved to S3. ( first snapshots takes a while, but afterwards its fine )

* Volumes VS Snapshots - Security
    * Snapshots of encrypted volumes are encrypted automatically.
    * Volumes that are restored from snapshots are encrypted automatically.
    * You can share snapshots with other AWS accounts, or publicly on the AWS market place, only if they are not encrypted.

* Snapshots of Root Device Volumes.
    * To create a snapshot for Amazon EBS volume that serve as root device, you should stop the instance before taking the snapshot ( but can be done on a running instance ).

* EBS vs Instance Store Volumes
    * Instance Store volumes are sometimes called Ephemeral Storage.
    * Instance Store volumes cannot be stopped, If the underlying host fails, you will loose your data.
    * EBS backed instances can be stopped, You will not loose the data on this instance if it is stopped.
    * You can reboot both, and you will not loose your data.
    * By default, both ROOT volumes will be deleted on termination, however with EBS volumes, you can tell AWS to keep the root device volume. ( set a FLAG )

* How to take a snapshot from the RAID Array?
    * Problem - Take a snapshot, the snapshot excludes data held in the cache by applications and the OS. This tends not to matter on a single volume, however using multiple volumes in a RAID array, this can be a problem due to interdependencies of the array.
    * Solution - Take an application consistent snapshot.
        * Stop the application from writing to disk
        * Flush all caches to the disk.
            * Freeze the file system.
            * Unmount the RAID Array.
            * Shutdown the associated EC2 instance.
* Amazon Machine Images 
    * AMI's are regional - You can only launch an AMI from the region in which it is stored. However you can copy AMI's to other regions using the console, commandline or the Amazon EC2 API. 

* Cloudwatch Monitoring
    * Standard monitoring is enabled by default for EC2. ( Every 5 minutes )
    * You can enable Detailed Monitoring ( Every minute ).
    * **CloudWatch is for performance monitoring.**
    * **CloudTrail is for Auditing**

* What can you create with CloudWatch ?
    * Dashboards - Create awesome dashboards to see what is happening with your aws environment.
    * Alarms - Allows you to set alarms that notify you when particular thresholds are hit.
    * Events - CloudWatch Events help you to respond to state changes in your aws resources.
    * Logs - CloudWatch logs help you to aggregate, monitor, and store logs.

* Roles 
    * Roles are more secure than storing your access key and secret access key on individual EC2 instances.
    * Roles are much easier to manage than having secret access keys around in terms of security.
        * If you loose your security key, you will have to delete the old ones and create a new one.
    * Roles can now be assigned to an EC2 instance after it has been provisioned using both the commandline and the AWS console.
    * Roles are global

* Instance Metadata
    * Used to get information about an instance ( such as public IPV4 )
    * `curl http://169.254.169.254/latest/meta-data/` will all the available information.

* EFS
    * Support the Network File System Version 4 protocol (NFSv4)
    * You only pay for the storage you use ( no pre-provisioning required )
    * Can scale upto petabytes
    * Can support thousands of concurrent NFS connections
    * Data is stored across multiple AZ's within a region.
    * Read After Write Consistency

* Lambda
    * AWS lambda is a compute service where you can upload your code and create lambda function. AWS Lambda takes care of provisioning and managing the servers that you use to run the code. You dont have to worry about the operating systems, patching, scaling, etc. You can use Lambda in the following ways.
    * As an event driven compute service, AWS runs your code in response to events. These events could be changes to your data in an Amazon S3 bucket or an Amazon DynamoDB table.
    * As a compute service to run your code in response to HTTP requests using Amazon API gateway or API calls made using AWS SDK's. This is what we use at A Cloud Guru.





































