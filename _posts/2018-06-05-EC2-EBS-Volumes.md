---
  layout: post
  title: EC2 EBS Volumes
  subtitle: 
  tags: [ compute, storage ]
  categories: compute
  author: Eshan Shafeeq
  header_img: 
---
### LAB

Go to aws services, and then goto EC2. One the left side panel, select Volumes.

* The EBS volume and the EC2 instance has to be in the same availability zone, in order for the volume to be attached to the EC2 instance.
* All root volumes will have a snapshot id, which relates to the machine image its running.
* There will be no down time when you modify your volumes, ( change the Hard disk type / change the disk size ). You may run into performance issues.
* With standard volumes, you will not be able to modify the volumes. ( ST1 - pure magnetic )
* In order to spin up an EC2 instance with the same volume in another availability zone:
    1. Goto Actions and create a snapshot.
    2. Add the required information on the form and click create.
    3. Goto snapshots.
    4. Click on Actions and Select Create a Volume.
    5. You can select any volume type / volume size.
    6. Select any availability zone that you want.
    7. And attach it to the EC2 instance you want.

    * Create a snapshot of the EBS volume you would like to move to another EC2 instance, Create a volume from that snapshot.
    * You can go to snapshots and copy the snapshot to any other region, if you want to switch region.
    * You can create an image from that snapshot in order to boot from that volume.
    * Snapshots are normally used for backups, Where as Images are used to create new volumes.
    * Make sure when you create an image its an image of one volume, when you want to boot off from this image later on.
    * You can also create AMI's directly from the snapshots, and then move it to another region.

> Root Device is where the operating system is installed at.

### Volumes and Snapshots
* Volumes exists on EBS
    * Virtual Hard Disk
* Snapshots exist on S3.
    * When you go to S3, you will not be able to see any buckets with the snapshots in there.
    * Snapshots are copies of Volumes at a given time.
    * Taking the second snapshot would only save the state of the blocks that have been modified, and moved to S3.
    * Your first snapshot will take some time to create, after the first one it wont take that long anymore.
    * To create a snapshot of a Volume which serve as a Root Volume, you should stop the running instance. But it is possible to take a snapshot of the running instance Root Volume.
    * You can create AMI's from both Volumes and Snapshots.
    * You can change the EBS Volume sizes on the fly, including changing the size and storage type.
    * Volumes will **ALWAYS** be in the same availability zone as the EC2 Instance.
    * To move an EC2 volume from one Availability Zone/Region to another, take a snap or an image of it, then copy it to the new Availability Zone/Region.
    * Snapshots of encrypted volumes are encrypted automatically.
    * Volumes restored from encrypted snapshots are encrypted automatically.
    * You can share snapshots, but only if they are unecrypted.
        * These snapshots can be shared with other aws accounts or it can be made completely public.

> Do this lab at least 3 times!

    
