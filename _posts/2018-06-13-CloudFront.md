---
  layout: post
  title: CloudFront
  subtitle: What is CloudFront
  tags: [ storage, cloudfront, cdn, s3 ]
  categories: storage
  author: Eshan Shafeeq
  header_img: 
---


A content delivery network (CDN) is a system of distributed servers (network) that delivers webpages and other web content to a user based on the geographic locations of the user, the origin of the webpage and a content delivery server.

Amazon cloudfront can be used to deliver your entire website, including dynamic, static, streaming, and interactive content using a global network of edge locations. Requests for your content are automatically routed to the nearest edge location, so content is delivered with the best possible performance. 

Amazon CloudFront is optimized to work with other Amazon web services, like amazon simple storage service, amazon elastic cloud compute, amazon elastic load balancing, and amazon route 53. Amazon CloudFront also works seamlessly  with any Non-Aws origin server, which stores the original, definitive versions of your files.

### Key terminology
* **Edge Location** - This is the location where content will be cached. This is seperate to an AWS Region/AZ.
    * Edge Locations are not **READ-ONLY**. You can **WRITE** to them too. ( ie put an object on to them ). This will be replicated back to the origin server.
    * Objects are cached for the life of the TTL ( Time To Live )
    * You can clear cached objects, but you will be charged.
* **Origin** - This is the origin of all the files that the CDN will distribute. This can be either an S3 bucket, an EC2 Instance, an Elastic Load Balancer or Route53.
* **Distribution** - This is the name given to the CDN which consists of a collection of Edge Locations.
* **Web Distribution** - Typically used for Websites.
* **RTMP** - Used for Media Streaming.

### LAB 
* Create a bucket in s3 to be used with CloudFront.
* Upload an image to that bucket.
* Goto CloudFront and click on create distribution network.
* Click on get start under Web.
* Select the s3 bucket on the origin domain name. (dropdown menu)
* Select Yes for restricting bucket access.
* Create a new identity for bucket access.
* Update bucket policy to grant read permissions.
* Under default cache behaviour Viewer protocol policy Redirect HTTP to HTTPS
* Restrict Viewer Access ( Use signed urls or signed cookies ) if you want to have restrictions.
* Hit save and it should be deployed in around 15 minutes.
* You can also enable geo restrictions
    * either black countries or whitelist countries but not both.
* If you want to remove an object from the cache immedietely ( Costs MONEY ), you can do so by creating an Invalidation.
* After youre done with setting up, make sure you delete the distribution network because this does cost you money.
    * First select the distribution network, and click on disable (15 - 30) mins later you will be able to click on delete.

