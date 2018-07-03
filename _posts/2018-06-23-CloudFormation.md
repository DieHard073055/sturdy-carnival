---
  layout: post
  title: CloudFormation
  subtitle: 
  tags: 
  categories: 
  author: 
  header_img: 
---

### What is CloudFormation ?
One of the most powerful parts of AWS, CloudFormation allows you to take what was once traditional hardware infrastructure and convert it into code.

CloudFormation gives developers and system administrators an way to create and manage a collection of related AWS resources, provisioning and updating them in an orderly and predictable fashion.

You dont need to figure out the order for provisioning AWS services or the subtleties of making those dependencies work. CloudFormation takes care of this for you.

After the AWS resources are deployed, you can modify and update them in a controlled and prdictable way, in effect **applying version control to your AWS infrastructure the same way you do with your software.**

A **Cloud Formation Template** is essentially an architectural diagram and a **Cloud Formation Stack** is the end result of that diagram (i.e. what is actually provisioned ).

You create, update, and delete a collection of resources by creating, updating, and deleting stacks using CloudFormation templates.

CloudFormation templates are in **JSON** format or **YAML**.

### Elements of a template
* **Mandatory Elements**
    * List of AWS Resources and their associated configuration values.
* Optional Elements
    * The template's file format & version number
    * Template Parameters
        * The input values that are supplied at stack creation time. Limit of 60.

* Output values
    * The output values required once a stack has finished building ( such as the Public IP address, ELB address, etc) Limit of 60.

* List of data tables
    * Use to look up static configuration values such as AMI's etc.

### Simple Template
JSON
```json
{
    "Resources":{
        "HelloBucket":{
            "Type":"AWS::S3::Bucket"
        }
    }
}
```

YAML
```yaml
Resources:
    HelloBucket:
        Type: AWS::S3::Bucket
```


### Outputting Data
*You can use Fn:GetAtt to output data.*

```json
"PublicIP":{
    "Description":"Public IP address of the web server",
    "Value":{
        "Fn::GetAtt":[
            "WebServerHost","PublicIp"
        ]
    }
}
```

### Exam Tips
* By default the *"automatic rollback on error"* ferature is **ENABLED**.
* You are **CHARGED** for errors.
* CloudFormation is free.
* Stacks can wait for applications to be provisioned using the *"WaitCondition"*.
* You can use the function *Fn:GetAtt* to output data.
* Route53 completely supported. This includes creating *new* hosted zones or *updating* existing ones.
    * You can create A Records, Aliases etc.
* IAM Role Creation and Assignment is also supported.

* If customer is new to AWS use ElasticBeanstalk.
* If customer wants to convert their infrastructure into code, use CloudFormation.
