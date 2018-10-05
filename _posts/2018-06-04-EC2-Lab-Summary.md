---
  layout: post
  title: EC2-Lab-Summary
  subtitle: 
  tags: [compute, ec2, virtual machine, lab]
  categories: compute
  author: Eshan Shafeeq
  header_img: 
---

### Creating an EC2 Instance
1. Select a region which you want your EC2 instance to be at.
    * Older regions will have most of the different types of EC2 instances available, newer ones will have less.
2. Select an AMI right after clicking on "Launch Instance".
    * You have many flavours of AMI's available.
    1. Amazon Linux AMI
    2. Red Hat Enterprise Linux
    3. SUSE Linux Enterprise Server
    4. Ubuntu Server 16.04 LTS
    5. Microsoft Windows Server
    * Version numbers of the above will change new version get adapted.
    * Amazon linux AMI comes with all the required built in tools and SDK's installed. (Free Tier Eligible)
3. Choose an Instance Type
    * t2.micro (Free Tier Eligible)
4. Configure Instance Details
    * Main setup page for Ec2
    * Under VPC you can select one of the subnets, there is one subnet for every single availability zone. **You can never have one subnet that goes across multiple availability zones.**
    * Selecting an IAM Role (Optional)
    * Enable termination protection [ to prevent people from accidentally terminating the instance ]
    * Additional charges are applied for detailed monitoring.
    * Advanced details, you can pass in bootstrap scripts to automate tasks.
5. Add Storage
    * Select the required storage for the root volume.
    * by default the **root volume will be deleted**.
    * Volume = virtual harddisk
6. Set the tags
    * Help you to control costs.
    * Always do more than just name tags, drill down upto the department and staff id.
7. Configure Security Groups
    * Its a virtual firewall
    * Set the services you want to allow, [ ssh, http, https ] 
    * You can restrict services to only from your IP.
8. Review everything and Launch
    * Create a keypair.
    * Either upload your own public key or create your keypair on the web interface and download.
    * Hit launch instance.

### Connect to the running Instance

Use ssh to connect to your instance.
```shell 
ssh ec2-user@[your_ec2_instance_public_ip-address] -i [your_keypair.pem]
```
Once logged in, it maybe a good idea to update the AMI `sudo yum update`.

### Creating a web server

Install apache.
```shell
sudo yum install httpd
```

Create a `index.html` file in `/var/www/html/` and then add some *HTML* in the file.
```HTML
<h1>Hello everyone</h1>
```

Start and run apache
```shell
sudo service httpd start
```

head to your public ip address of your ec2 instance on your browser and you should be able to see the web server.

### Health Status Information
The bottom panel, on the tab `Status Checks`. It has the information about `System Status Check` and `Instance Status Check`. 
**System Status Check** : Check if aws is able to get network packets into the instance. If this status fails, theres probably a problem with the aws infrastructure.
**Instance Status** : This check verifies if the instance's operating system is accepting traffic.

### Monitoring
The bottom panel, on the tab `Monitoring`. You have system metrics which are updated every 5 minutes. You can enable detailed monitoring (which can cost a bit extra).

All the different metrics here are accesible through cloud watch.

### Lab Summary
* All newly created Instances have **termination protection** turned off by default, you must turn it on.
* On an EBS-backed instance, the default action is for the root EBS volume to be **deleted** when the instance is terminated.
* EBS Root Volumes of your **DEFAULT AMI's cannot be encrypted.** You can also use third party tool (such as bitlocker etc) to encrypt the root volume, or this can be done when creating AMI's (lab to follow) in the AWS console or using the API.
* Additional Volumes can be encrypted.


