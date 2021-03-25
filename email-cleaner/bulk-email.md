# Bulk Email

Bulk email cleaning is a process where you can upload any .txt / .csv / .xlsx file for email cleaning. At one time the only one file can be accepted over API.

The file must be less than 15MB in size and includes a maximum of 100,000 emails.

The header of the email column inside file should be "emails" for identification of email list inside the file.

{% api-method method="post" host="https://api.saino.io" path="/api/apis/email-cleaning/verify-bulk" %}
{% api-method-summary %}
Bulk Email Clean
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to upload bulk email file for cleaning
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="token" type="string" required=false %}
The token provided by Saino application
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="file" type="object" required=false %}
your .csv/.txt/.xlsx file in form-data format \(blob format\)
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
     status: "success",
     bulk_id: 1002,
     message: "Successfully added in queue"
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
{% tab title="Nodejs" %}
```text
var request = require('request');
var fs = require('fs');
var options = {
  'method': 'POST',
  'url': 'https://api.saino.io/api/apis/email-cleaning/verify-bulk',
  'headers': {
    'token': '7yq7x1hlydj8hyxccfg6dy6rdmc61al5411mtwid609584683074',
  },
  formData: {
    'file': {
      'value': fs.createReadStream('/path-to-file/test1.csv'),
      'options': {
        'filename': 'test1.csv',
        'contentType': null
      }
    }
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
$request->setUrl('https://api.saino.io/api/apis/email-cleaning/verify-bulk');
$request->setMethod(HTTP_Request2::METHOD_POST);
$request->setConfig(array(
  'follow_redirects' => TRUE
));
$request->setHeader(array(
  'token' => '7yq7x1hlydj8hyxccfjo13011m==/tw121609584683074',
));
$request->addUpload('file', '/path-to-file/test1.csv', 'test1.csv', '<Content-Type Header>');
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
var form = new FormData();
form.append("file", fileInput.files[0], "test1.csv");

var settings = {
  "url": "https://api.saino.io/api/apis/email-cleaning/verify-bulk",
  "method": "POST",
  "timeout": 0,
  "headers": {
    "token": "7yq7x1hlydj8hy6rdmc61al5411609584683074",
  },
  "processData": false,
  "mimeType": "multipart/form-data",
  "contentType": false,
  "data": form
};

$.ajax(settings).done(function (response) {
  console.log(response);
});
```
{% endtab %}

{% tab title="Python" %}
```
import requests

url = "https://api.saino.io/api/apis/email-cleaning/verify-bulk"

payload={}
files=[
  ('file',('test1.csv',open('/path-to-file/test1.csv','rb'),'text/csv'))
]
headers = {
  'token': '7yq7x1hlydj8hyxccfjo1969f46e8v121609584683074',
}

response = requests.request("POST", url, headers=headers, data=payload, files=files)

print(response.text)

```
{% endtab %}
{% endtabs %}

