---
  layout: post
  title: Web Identity Providers
  subtitle: 
  tags: [ security, database, social, openid, assumerolewithwebidentity, dynamodb ]
  categories: database
  author: Eshan Shafeeq
  header_img: 
---

### Web Identity Providers

You can authenticate users using **Web Identity Providers** ( such as Facebook, Google, Amazon, or any other Open-ID Connect-compatible Identity provider). This is done using AssumeRoleWithWebIdentity API.

You will need to create a role first

1. User Authenticates With WebIDProvider
2. WebIDProvider gives you a Web Identity Token.
3. Do the AssumeRoleWithWebIdentity Request to AWS SecurityTokenService (STS)
4. AWS (STS) gives back Temporary Security Credentials ( Defaults 1 hour )
    * Access Key ID, Secret Access Key, Session Token.
    * Expiration ( Time limit )
    * AssumeRoleID
    * SubjectFromWebIdentityToken ( The unique ID that appears in an IAM policy variable for this particular identity provider )
5. Using these credentials, you can access dynamodb.

---

#### Steps taken to authenticate
1. User Authenticates with the ID provider
2. They are passed a Token by their ID provider.
3. Your code calls **AssumeRoleWithWebIdentity** API and provides the providers token and specifies the ARN for the IAM Role.
4. App can now access DynamoDB from between 15 minutes to 1 hour (default is 1 hour)

