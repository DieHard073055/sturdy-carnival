---
  layout: post
  title: Serverless Website
  subtitle: Create a Serverless Website using S3 + API Gateway + Lambda
  tags: [ compute, storage, apigateway, s3, lambda, serverless ]
  categories: storage
  author: Eshan Shafeeq
  header_img: 
---


This will be example of the simplest serverless website possible.
### Instructions
* First we will need to create a lambda function 
    * Select python 3.6 for the language
    * add the following code to your lambda

```python

    def lambda_handler(event, context):
    print("In lambda_handler")

    resp = {
        "statusCode":200,
        "headers" : {
            "Access-Control-Allow-Origin":"*",
        },
        "body":"This response is from a lambda function running in ohio!",
    }

    return resp

```

* Now set the trigger for your lambda function as API Gateway.
    * Give it any name you want.
    * Save your lambda settings
    * Go to API Gateway and make sure its a get request.
    * Go to stages and get the GET method URL.
    * See if the URL gives back the response you expect.
* Create a bucket in S3 with static website hosting
* add the following index.html

```html

<html>
<script>
function request(){
    var xhttp = new XMLHttpRequest();
    xhttp.onreadystatechange = function(){
        if( this.readyState == 4 && this.status == 200 ){
            document.getElementById("demo").innerHTML = this.responseText;
        }
    };
    xhttp.open("GET","API GATEWAY URL", true);
    xhttp.send();
}
</script>
<body>
    <div align="center"><br><br><br><br>
    <h1>Hello people</h1>
    <button onclick="request()">Click me!</button>
    <div id="demo"></div>

</body>
</html>

```

* If you have added the API Gateway url in the code above, It should work accordingly.

And that is how you build a serverless website with S3, Lambda and API Gateway!

