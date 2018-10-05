---
  layout: post
  title: Route53 - Routing Policies
  subtitle: 
  tags: 
  categories: 
  author: 
  header_img: 
---
### Types of Routing Policies
* Simple
* Weighted
* Latency
* Failover
* Geolocation

### Simple
This is the default routing policy when you create a new record set. This is most commonly used when you have a single resource that performs a given function for your domain, for example, one web server that serves content for the http://acloud.guru website.

### Weighted 
This allows you to split your traffic based on different weights assigned. For example you can set 10% of your traffic to go to US-EAST-1 and 90% of your traffic to go to EU-WEST-1. This doesnt do it by request, it does via the length of the day. Usually used for testing your new website.

### Latency
Latency based routing allows you to route your traffic based on the lowest network latency for your end user. ( ie which region will give them the fastest response time). To use latency-based routing you create a latency resource record set for the Amazon EC2 ( or ELB ) resource in each region that hosts your website. When Amazon Route 53 receives a query for your site, it selects the latency resource record set for the region that gives the user the lowest latency. Route53 then responds with the value associated with that resource set.

### Failover
Failover routing policies are used when you want to create an active/passive setup. For example you may want your primary site to be in EU-WEST-2 and your secondary DR Site in AP-SOUTHEAST-2. Route53 will monitor the health of your primary site using a health check. A health check monitors the health of your endpoints.

### Geolocation
Allows you to direct your traffic to different routes based on the geographic location of your users. ( location from which the DNS queries originate from ). For example, you might want all queries from Europe to be routed to a fleet of EC2 instances that are specifically configured for your European customers. These servers may have the local language of your European customers and all prices are displayed in Euros.

### DNS Exam Tips
**Elastic Load Balancers never have an ipv4 address.**
* Understand the difference between an Alias Record and a CNAME.
* If youre ever given the choice, always choose an Alias Record over a CNAME, because it dosent cost money. 
* Remember the different routing polices.
