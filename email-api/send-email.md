# Send Email

{% api-method method="post" host="https://api.saino.io" path="/api/apis/email/send" %}
{% api-method-summary %}
Send Email
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to send an email.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
It is a bearer authentication token to validate request coming from a valid user or not. You can get this token from Saino first account from API keys section.  
  
if you passing  programmtically then follow below approach:   
  
Authorization: "Bearer " + API\_KEY 
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="to" type="array" required=true %}
This is **to** contain **email ids** where you need to send emails. you can add multiple email ids where you need to send emails
{% endapi-method-parameter %}

{% api-method-parameter name="subject" type="string" required=true %}
This contains email subject
{% endapi-method-parameter %}

{% api-method-parameter name="from" type="string" required=true %}
This is a from email id. you can assigned only verified email id. you can verify from email id from sainofirst dashboard by below-specified section.  
dashboard -&gt; bulk email -&gt; settings-&gt; domain
{% endapi-method-parameter %}

{% api-method-parameter name="fromName" type="string" required=true %}
Display name for from email address
{% endapi-method-parameter %}

{% api-method-parameter name="bodyHtml" type="string" required=false %}
This field used to send html content in email   
**either bodyHtml or bodyText is required**
{% endapi-method-parameter %}

{% api-method-parameter name="bodyText" type="string" required=false %}
This field used to send normal text content in email  
**either bodyHtml or bodyText is required**
{% endapi-method-parameter %}

{% api-method-parameter name="trackClicks" type="boolean" required=false %}
Should the click be tracked? If no value has been provided, Account's default setting will be used.
{% endapi-method-parameter %}

{% api-method-parameter name="trackOpens" type="boolean" required=false %}
Should the opens be tracked? If no value has been provided, Account's default setting will be used
{% endapi-method-parameter %}

{% api-method-parameter name="replyToEmail" type="string" required=false %}
Email address to reply to
{% endapi-method-parameter %}

{% api-method-parameter name="replyToName" type="string" required=false %}
Name to replay to name
{% endapi-method-parameter %}

{% api-method-parameter name="attachments" type="array" required=false %}
An array of ID's of attachments.  
Note: you can get attachment id from uploading attachment by upload attachment API
{% endapi-method-parameter %}

{% api-method-parameter name="callbackUrl" type="string" required=false %}
Call back where you received notifications related to email.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```javascript
{ 
    status: true, 
    message: "Success",
    campaignId:"8asd6sx-as6tasvdt-asdg532v"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Whenever some fields missings or invalid values present. 
{% endapi-method-response-example-description %}

```javascript
{ 
    status: false, 
    error: "Some required fields missings" 
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Whener ver user access with invalid authorasation key.
{% endapi-method-response-example-description %}

```javascript
{    
    message: "Unauthorised" 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Callback Url response

below is the notification response received in provided callback url related to each email id.

```javascript
{
    emailId: "test@test.com",  //provided to email id
    status: "sent/opened/clicked/bounce/complaint/unsubscribed", //this is email status
    campaignId: "8asd6sx-as6tasvdt-asdg532v"  //campaign id to identify
}
```

## Examples

{% tabs %}
{% tab title="NodeJs" %}
```javascript
var axios = require('axios');
var data = JSON.stringify(
  {
    "to":["test@gmail.com"],
    "subject":"API test 1",
    "from":"test@domain.com",
    "fromName":"sahil",
    "bodyHtml":"<h1>Test 1</h1>",
    "trackClicks":true,
    "trackOpens":true,
    "replyToEmail":"test2@domain2.com",
    "attachments":[],
    "replyToName":"sam",
    "bodyText":"Just Text Email",
    "callbackUrl":"https://domain.com/webhook"
  }
);

var config = {
  method: 'post',
  url: 'https://api.saino.io/api/apis/email/send',
  headers: { 
    'Authorization': 'Bearer 808ciij4p18351yml==/pitzkg67bizz0qce1599144457846', 
    'Content-Type': 'application/json'
  },
  data : data
};

axios(config).then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});

```
{% endtab %}

{% tab title="PHP" %}
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.saino.io/api/apis/email/send",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS =>"{\n     \"to\":[\"test@gmail.com\"], \n     \"subject\":\"API test 1\", \n     \"from\":\"test@domain.com\", \n     \"fromName\":\"sainofirst\", \n     \"bodyHtml\":\"<h1>Test 1</h1>\", \n     \"trackClicks\":true, \n     \"trackOpens\":true, \n     \"replyToEmail\":\"test2@sainofirst.com\", \n     \"attachments\":[], \n     \"replyToName\":\"sainofirst2\", \n     \"bodyText\":\"Just Text Email\",\n     \"callbackUrl\":\"https://domain.com/webhook\"\n}",
  CURLOPT_HTTPHEADER => array(
    "Authorization: Bearer 808ciij4p1835zba8ykvkw9p==/pitzkg67bizz0qce1599144457846",
    "Content-Type: application/json"
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

```
{% endtab %}

{% tab title="Python" %}
```
import requests

url = "https://api.saino.io/api/apis/email/send"

payload = "{\n     \"to\":[\"test@gmail.com\"], \n     \"subject\":\"API test 1\", \n     \"from\":\"test@domain.com\", \n     \"fromName\":\"sainofirst\", \n     \"bodyHtml\":\"<h1>Test 1</h1>\", \n     \"trackClicks\":true, \n     \"trackOpens\":true, \n     \"replyToEmail\":\"test2@sainofirst.com\", \n     \"attachments\":[], \n     \"replyToName\":\"sainofirst2\", \n     \"bodyText\":\"Just Text Email\",\n     \"callbackUrl\":\"https://domain.com/webhook\"\n}"
headers = {
  'Authorization': 'Bearer 808ciij4p1835h8gkybgzba8ykvkw9pz0qce1599144457846',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))

```
{% endtab %}

{% tab title="C" %}
```c
CURL *curl;
CURLcode res;
curl = curl_easy_init();
if(curl) {
  curl_easy_setopt(curl, CURLOPT_CUSTOMREQUEST, "POST");
  curl_easy_setopt(curl, CURLOPT_URL, "https://api.saino.io/api/apis/email/send");
  curl_easy_setopt(curl, CURLOPT_FOLLOWLOCATION, 1L);
  curl_easy_setopt(curl, CURLOPT_DEFAULT_PROTOCOL, "https");
  struct curl_slist *headers = NULL;
  headers = curl_slist_append(headers, "Authorization: Bearer 808ciij4p18351v9rh8gkybgzba8ykvkw9p==/pitzkg67bizz0q99144457846");
  headers = curl_slist_append(headers, "Content-Type: application/json");
  curl_easy_setopt(curl, CURLOPT_HTTPHEADER, headers);
  const char *data = "{\n     \"to\":[\"test@gmail.com\"], \n     \"subject\":\"API test 1\", \n     \"from\":\"test@domain.com\", \n     \"fromName\":\"sainofirst\", \n     \"bodyHtml\":\"<h1>Test 1</h1>\", \n     \"trackClicks\":true, \n     \"trackOpens\":true, \n     \"replyToEmail\":\"test2@sainofirst.com\", \n     \"attachments\":[], \n     \"replyToName\":\"sainofirst2\", \n     \"bodyText\":\"Just Text Email\",\n     \"callbackUrl\":\"https://domain.com/webhook\"\n}";
  curl_easy_setopt(curl, CURLOPT_POSTFIELDS, data);
  res = curl_easy_perform(curl);
}
curl_easy_cleanup(curl);

```
{% endtab %}

{% tab title="C\#" %}
```csharp
var client = new RestClient("https://api.saino.io/api/apis/email/send");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("Authorization", "Bearer 808ciijv9rzg5h8gkybgzba8ykvkw9p==/dsaddadasdda");
request.AddHeader("Content-Type", "application/json");
request.AddParameter("application/json", "{\n     \"to\":[\"test@gmail.com\"], \n     \"subject\":\"API test 1\", \n     \"from\":\"test@domain.com\", \n     \"fromName\":\"sainofirst\", \n     \"bodyHtml\":\"<h1>Test 1</h1>\", \n     \"trackClicks\":true, \n     \"trackOpens\":true, \n     \"replyToEmail\":\"test2@sainofirst.com\", \n     \"attachments\":[], \n     \"replyToName\":\"sainofirst2\", \n     \"bodyText\":\"Just Text Email\",\n     \"callbackUrl\":\"https://domain.com/webhook\"\n}",  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```
{% endtab %}

{% tab title="HTTP" %}
```http
POST /api/apis/email/send HTTP/1.1
Host: api.saino.io
Authorization: Bearer 808ciij4p18351ymliiznhybgzba8ykvkw9p==/qce1599144457846
Content-Type: application/json

{
     "to":["test@gmail.com"], 
     "subject":"API test 1", 
     "from":"test@domain.com", 
     "fromName":"sainofirst", 
     "bodyHtml":"<h1>Test 1</h1>", 
     "trackClicks":true, 
     "trackOpens":true, 
     "replyToEmail":"test2@sainofirst.com", 
     "attachments":[], 
     "replyToName":"sainofirst2", 
     "bodyText":"Just Text Email",
     "callbackUrl":"https://domain.com/webhook"
}
```
{% endtab %}

{% tab title="JAVA" %}
```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\n     \"to\":[\"test@gmail.com\"], \n     \"subject\":\"API test 1\", \n     \"from\":\"test@domain.com\", \n     \"fromName\":\"sainofirst\", \n     \"bodyHtml\":\"<h1>Test 1</h1>\", \n     \"trackClicks\":true, \n     \"trackOpens\":true, \n     \"replyToEmail\":\"test2@sainofirst.com\", \n     \"attachments\":[], \n     \"replyToName\":\"sainofirst2\", \n     \"bodyText\":\"Just Text Email\",\n     \"callbackUrl\":\"https://domain.com/webhook\"\n}");
Request request = new Request.Builder()
  .url("https://api.saino.io/api/apis/email/send")
  .method("POST", body)
  .addHeader("Authorization", "Bearer 808ciij4p183hrkv9rzg5h8gkybgzba8yasdp==/sadsd")
  .addHeader("Content-Type", "application/json")
  .build();
Response response = client.newCall(request).execute();
```
{% endtab %}

{% tab title="SWIFT" %}
```swift
import Foundation

var semaphore = DispatchSemaphore (value: 0)

let parameters = "{\n     \"to\":[\"test@gmail.com\"], \n     \"subject\":\"API test 1\", \n     \"from\":\"test@domain.com\", \n     \"fromName\":\"sainofirst\", \n     \"bodyHtml\":\"<h1>Test 1</h1>\", \n     \"trackClicks\":true, \n     \"trackOpens\":true, \n     \"replyToEmail\":\"test2@sainofirst.com\", \n     \"attachments\":[], \n     \"replyToName\":\"sainofirst2\", \n     \"bodyText\":\"Just Text Email\",\n     \"callbackUrl\":\"https://domain.com/webhook\"\n}"
let postData = parameters.data(using: .utf8)

var request = URLRequest(url: URL(string: "https://api.saino.io/api/apis/email/send")!,timeoutInterval: Double.infinity)
request.addValue("Bearer 808ciij4pzba8ykvkw9p==/pitzkg99144457846", forHTTPHeaderField: "Authorization")
request.addValue("application/json", forHTTPHeaderField: "Content-Type")

request.httpMethod = "POST"
request.httpBody = postData

let task = URLSession.shared.dataTask(with: request) { data, response, error in 
  guard let data = data else {
    print(String(describing: error))
    return
  }
  print(String(data: data, encoding: .utf8)!)
  semaphore.signal()
}

task.resume()
semaphore.wait()
```
{% endtab %}
{% endtabs %}

