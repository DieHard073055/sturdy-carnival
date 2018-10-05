---
  layout: post
  title: EC2 AWS CLI DEV
  subtitle: EC2 AWS CLI Developer Exam Tips
  tags: [ examtips, compute, awscli, ec2, developer ]
  categories: compute
  author: Eshan Shafeeq
  header_img: 
---

### To create a new ec2 instance

Inorder to create a new ec2 instance from the commandline, we first need to know which AMI we want to use. We could pass the option `describe-images` to the aws cli and we can get the list. But that would return you a huge list. To list out the images from amazon you can use the following command.

```shell
aws ec2 describe-images --owners amazon --filters "Name=platform,Values=Linux1" "Name=root-device-type,Values=ebs"
```
you can go to the console, get the SubnetID of the ec2 instance you are logged in. 
you also have to make sure you have a keypair on aws. Try the following command launch your instance.

```shell
aws ec2 run-instances --image-id ami-165a0876 --count 1 --instance-type t2.micro --key-name MyKeyPair --security-groups-ids sg-d03bafb7 --subnet-id subnet123abc
```

It should have provisioned your ec2 instance if you do not have any problems in your command.

Now to terminate instances, all you need to do is grab the instance ids and then type the following command.

```shell
aws ec2 terminate-instances --instance-ids [instance id]
```

Be careful when you issue that command, it will completely destroy your ec2 instance.

### Commands

| Command | Description |
|---------|-------------|
| `aws ec2 describe-instances` | will show all the information about your instances |
| `aws ec2 describe-images` | will show all the information about all the available images. Be aware this will spam your terminal with a never ending list of json |
| `aws ec2 run-instances` | will create a new instance and launch |
| `aws ec2 start-instances` | will start a stopped instance |

**Dont get confused about start-instances and run-instances** start instances will not create a new instance! only run instance would create a new instance. And start instance will only start a stopped instance.


