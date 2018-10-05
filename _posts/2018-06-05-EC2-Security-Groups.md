---
  layout: post
  title: EC2 Security Groups
  subtitle: 
  tags: [firewall, security, networking, virtual firewall] 
  categories: compute
  author: Eshan Shafeeq
  header_img: 
---

A Security Group is a Virtual Firewall, which controls traffic in and out of your ec2 instance. Ec2 instances are launched with one or more security groups attached to it. Multiple security groups can be applied to one ec2 instance. This is also the first line of defence against any security threats.

* Any change to the security group or implementing rules across security groups, comes into effect immedietly. 
* Security groups are stateful, any rules added as inbound rules allows outbound rules.
* You are not able to deny any traffic, you can only allow traffic since all traffic is blocked by default.
* Your ec2 instances will be able to communicate with each other if they have the default security group attached to them, regarless of the region they are based off of.
* If you want to attach more than one security group to an instance which is already running, go to actions->Networking->Change Security Groups-> and check all the security groups you want to attach for the instance.

### Summary
* All inbound traffic is blocked by default.
* All outbound traffic is allowed.
* Changes to security group takes effect immediately.
* You can any number of EC2 instances within a security group.
* You can have multiple security groups attached to an instance.
* Security groups are stateful.
* You cannot block specific IP Addresses using security groups, instead use Network Access Control Lists.
* You can specify allow rules, but not deny rules.

