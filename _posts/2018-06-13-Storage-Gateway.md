---
  layout: post
  title: Storage Gateway
  subtitle: 
  tags: [ storage, storagegateway, secure ]
  categories: storage
  author: Eshan Shafeeq
  header_img: 
---

AWS Storage Gateway, is a service that connects an on-premises software appliance with cloud-based storage to provide seamless and secure integration between an organization's on premises IT environment and AWS's storage infrastructure. The service enables you to securely store data to the AWS cloud for scalable and cost-effective storage.

AWS Storage Gateway Software Appliance is available for download as a virtual machine (VM) image that you install on a host in your data center. Storage Gateway support either VMware ESXi or Microsoft Hyper-V. Once youve installed your gateway and associated it with your AWS account though the activation process, you use the AWS Management Console to create the storage gateway option that is right for you.

### 4 types of storage gateways
* File Gateway (NFS)
* Allows you store flat files in S3 ( word documents, pictures, pdf's, etc )
* Volume Gateways ( iSCSI ) This for block based storage, maybe a volume attached to a VM.
    * Stored Volume ( Gateway Stored Volumes )
    * Cached Volume ( Gateway Cached Volumes )
* Tape Gateway ( VTL ) Backup and archiving solution.

### File Gateway
Files are stored as objects in your S3 buckets, accessed through a Network File System (NFS) mount point. Ownership, permissions, and timestamps are durably stored in S3 in the user-metadata of the object associated with the file. Once objects are transferred to S3, they can be managed as native S3 objects, and bucket policies such as versioning, lifecycle management, and cross-region replication apply directly to objects stored in your bucket.

### Volume Gateway
The volume interface presents your applications with disks volumes using iSCSI block protocol. Data written to these volumes can be asynchronously backed up as point-in-time snapshots of your volumes, and stored in the cloud as Amazon EBS snapshots. Snapshots are incremental backups that capture only changed blocks. All snapshots storage is also compressed to minimize your storage charges.

##### Stored Volumes
Stored volumes let you store your primary data locally, while asynchronously backing up that data to AWS. Stored volumes provide your on-premises applications with low-latency access to their entire datasets, while providing durable, off-site backups. You can create storage volumes and mount them as iSCSI devices from your on-premises application servers. Data written to your stored volumes is asynchronously backed upto Amazon Simple Storage Service ( Amazon S3 ) in the form of Amazon Elastic Block Store ( Amazon EBS ) snapshots. 1GB - 16TB in size for Stored Volumes.

##### Cached Volumes
Cached volumes lets you use Amazon Simple Storage Service ( Amazon S3 ) as your primary data storage while retaining frequently accessed data locally in your storage gateway. Cached volumes minimize the need to scale your on-premises storage infrastructure, while still providing your applications with low-latency access to their frequently accessed data. You can create storage volumes upto 32 TB in size and attach to them as iSCSI devices from your on-premises application servers. Your gateway stores data that you write to these volumes in Amazon S3 and retains recently read data in your on-premises storage gateway's cache and upload buffer storage. 1GB - 32 TB in size for Cached Volumes.

##### Taped Gateway
Tape Gateway offers a durable, cost-effective solution to archive your data in the AWS Cloud. The VTL interface it provides lets you leverage your existing tape-based backup application infrastructure to store data on virtual tape cartridges that you create on your tape gateway. Each tape gateway is preconfigured with a media changer and tape drives, which are available to your existing client backup applications as iSCSI devies. You add tape cartridges as you to archive your data. Supported by NetBackup, Backup Exec, Veam etc.


### Exam Tips
* File Gateway - For flat files, stored directly on S3 - Not os's
* Volumes Gateways (block based storage)
    * Stored Volumes - Entire Dataset is stored on site is asynchronously backed up to S3.
    * Cached Volumes - Entire Dataset is stored on S3 and most frequently accessed data is kept on site.
* Gateway Virtual Tape Library ( VTL )
    * Used for backup and uses popular backup applications like NetBackup, Backup Exec, Veam etc.


