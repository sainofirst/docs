# Single Email

{% api-method method="get" host="https://api.saino.io" path="/api/apis/email-cleaning/verify-single" %}
{% api-method-summary %}
Verify Signle Email
{% endapi-method-summary %}

{% api-method-description %}
This Endpoint you will used for verifying single email id
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="token" type="string" required=false %}
The token provided by the saino application
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="email" type="string" required=false %}
Email id which you want to verify.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
   "data":{
      "email":"any@gmail.com",
      "free_email":"true",
      "result":"Safe to Send / Unsafe to Send",
      "status":"Deliverable"
   },
   "status":"success"
}

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    status: "failed",
    error: "" //error message
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Examples

{% tabs %}
{% tab title="NodeJs" %}
```text
var axios = require('axios');

var config = {
  method: 'get',
  url: 'https://api.saino.io/api/apis/email-cleaning/verify-single?email=user@domain.com',
  headers: { 
    'token': '7yq7x1hlydj8hyxccfjo130m7usey6g6dyrdmc61al5411m==/twidh21609584683074'
  }
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});

```
{% endtab %}

{% tab title="PHP-HTTP" %}
```
<?php
require_once 'HTTP/Request2.php';
$request = new HTTP_Request2();
$request->setUrl('https://testt.gomnp.com/api/apis/email-cleaning/verify-single?email=usr@domain.com');
$request->setMethod(HTTP_Request2::METHOD_GET);
$request->setConfig(array(
  'follow_redirects' => TRUE
));
$request->setHeader(array(
  'token' => '7yq7x1hlydj8hyxccfjo130msey6g6d5411m==/tw084683074'
));
try {
  $response = $request->send();
  if ($response->getStatus() == 200) {
    echo $response->getBody();
  }
  else {
    echo 'Unexpected HTTP status: ' . $response->getStatus() . ' ' .
    $response->getReasonPhrase();
  }
}
catch(HTTP_Request2_Exception $e) {
  echo 'Error: ' . $e->getMessage();
}
```
{% endtab %}

{% tab title="JQuery" %}
```
var settings = {
  "url": "https://api.saino.io/api/apis/email-cleaning/verify-single?email=user@doamin.com",
  "method": "GET",
  "timeout": 0,
  "headers": {
    "token": "7yq7x1hlydj8hyxccfjo13rdmc61al5411m==/twi9584683074"
  },
};

$.ajax(settings).done(function (response) {
  console.log(response);
});
```
{% endtab %}

{% tab title="Python" %}
```
import requests

url = "https://api.saino.io/api/apis/email-cleaning/verify-single?email=sahil@sainofirst.com"

payload={}
headers = {
  'token': '7yq7x1hlydj8hyxccfjo130m6e8v121609584683074',
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

```
{% endtab %}
{% endtabs %}



