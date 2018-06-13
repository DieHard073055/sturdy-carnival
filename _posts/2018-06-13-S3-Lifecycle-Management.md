---
  layout: post
  title: S3 Lifecycle Management
  subtitle: 
  tags: [ storage, s3, lifecycle, management ]
  categories: storage
  author: Eshan Shafeeq
  header_img: 
---

* Can be used in conjunction with versioning
* Can be applied to current versions and previous versions.
* Following actions can now be done:
    * Transition to the standard infrequently accessed storage class
        * File sizes have to be bigger than 128kb and a minimum 30 days after creation.
        * Archive it to glacier storage class ( 30 days after IA, if relevant )
        * Permanently Delete

