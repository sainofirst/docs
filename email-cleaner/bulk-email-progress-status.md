# Bulk Email Progress / Status

{% api-method method="get" host="https://api.saino.io" path="/api/apis/email-cleaning/bulk-progress" %}
{% api-method-summary %}
Get Bulk Email Progress Status
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get progress of bulk email cleaning progress.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="token" type="string" required=false %}
The token provided by saino application.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="bulk\_id" type="integer" required=false %}
Bulk process id which you got from bullk email cleaning api response.  
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "data": {
        "bulk_id": 1002,
        "status": "completed",
        "percentage": 100,
        "download_link": "https://sfeclean.s3.ap-south-1.amazonaws.com/email-cleaner/report/final_verified_8961ea-2017-421a-a919-a1b2183ad86f_test1.csv.csv"
    },
    "status": "success"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
     status: "failed",
     error: '' //errors
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
var request = require('request');
var options = {
  'method': 'GET',
  'url': 'https://api.saino.io/api/apis/email-cleaning/bulk-progress?bulk_id=95',
  'headers': {
    'token': '7yq7x1hlydj8hyxccf61al5411m==/twidh969f9584683074',
  }
};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});

```
{% endtab %}

{% tab title="PHP" %}
```
<?php
require_once 'HTTP/Request2.php';
$request = new HTTP_Request2();
$request->setUrl('https://api.saino.io/api/apis/email-cleaning/bulk-progress?bulk_id=95');
$request->setMethod(HTTP_Request2::METHOD_GET);
$request->setConfig(array(
  'follow_redirects' => TRUE
));
$request->setHeader(array(
  'token' => '7yq7x1hlydj8hyxccfjomc61al5411m==/twid21609584683074'
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

{% tab title="JQUERY" %}
```
var settings = {
  "url": "https://api.saino.io/api/apis/email-cleaning/bulk-progress?bulk_id=95",
  "method": "GET",
  "timeout": 0,
  "headers": {
    "token": "7yq7x1hlydj8hyxccfjo130mc61al5411m==/twi46e8v584683074",
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

url = "https://api.saino.io/api/apis/email-cleaning/bulk-progress?bulk_id=95"

payload={}
headers = {
  'token': '7yq7x1hlydj8hyxccfjordmc61al8v121609584683074',
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

```
{% endtab %}
{% endtabs %}



