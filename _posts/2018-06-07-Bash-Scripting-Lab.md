---
  layout: post
  title: Bash Scripting Lab
  subtitle: Writing bash scripts to manipulate the aws resources
  tags: [ bashscripting, lab, ec2, s3 ]
  categories: compute
  author: Eshan Shafeeq
  header_img: 
---

In this lab we are going to pass a bash script to the ec2 instance before it is launched to automate some of the tasks we want the instance to execute before we ssh in.

### Instructions

Create an ec2 instance to launch.
Make sure you assign the role s3-admin-access to this instance.
On the tab `3. Configure Instance` -> Advanced Details -> User Data `!`. Make sure As text option is selected. And then add then pass the following bash script to it.

```shell
#!/bin/bash

# Log file to log all the events
LOGFILE=/home/ec2-user/ONBOOT.log


# Install updates to the server
sudo yum update -y 2>&1 >> $LOGFILE

# Install apache
sudo yum install httpd -y 2>&1 >> $LOGFILE

# Start the apache service and set the service to run on boot
sudo service httpd start 2>&1 >> $LOGFILE
sudo chkconfig httpd on 2>&1 >> $LOGFILE

# Copy website from s3 to /var/www/html
sudo aws s3 cp --recursive s3://[bucketname] /var/www/html/ 2&1 >> $LOGFILE

echo "Startup script done installing essentials" >> $LOGFILE
```

When the instance gets launched, It should have setup the webserver and your file will be available when you head to the instance ip address on the browser. Also after you login, you be able to see the execution logs on the home directory. If anything did go wrong it should be on the logs.
