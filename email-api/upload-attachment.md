# Upload Attachment

Below API used to upload attachments in sainofirst platform.  
Purpose of API is whenever the user wants to send an attachment in the email. user need to upload attachment in sainofirst platform first. sainofirst will provide id represents to attachment. and the user can send this id in send email API's attachment field to send attachment along with the email.  

{% api-method method="post" host="https://api.saino.io" path="/api/apis/email/upload-attachment" %}
{% api-method-summary %}
Upload Attachment 
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="content-type" type="string" required=false %}
multipart/form-data with document boundary
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=false %}
It is a bearer Authorization token to validate request coming from a valid user or not. you can get this token from sainofirst account from API keys section.   
  
If you passing programatically then follow below approch:  
  
Authorization: "Bearer "+API\_KEY
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="file" type="object" required=true %}
binary file data
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    status: true, 
    data: { 
        attachment_id: 100,  //id used in send email
        file_size: 100,   //in bytes
        content_type: "<<file_content_type>>", 
        filename: "<<file_name>>" 
    } 
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=302 %}
{% api-method-response-example-description %}
Whenever Invalid data comes
{% endapi-method-response-example-description %}

```javascript
{ 
    status: false, 
    error: "Not able to process your request" 
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Whenever user access with invalid authorization key
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

## Examples

{% tabs %}
{% tab title="NodeJs" %}
```javascript
var axios = require('axios');
var FormData = require('form-data');
var fs = require('fs');
var data = new FormData();
data.append('file', fs.createReadStream('/path-to-file'));

var config = {
  method: 'post',
  url: 'https://api.saino.io/api/apis/email/upload-attachment',
  headers: { 
    'Authorization': 'Bearer 808ciij4p1g5h8gkybgzba8ykvkw9pitzkg67bizz0qce', 
    ...data.getHeaders()
  },
  data : data
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

{% tab title="PHP" %}
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.saino.io/api/apis/email/upload-attachment",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('file'=> new CURLFILE('/path-to-file')),
  CURLOPT_HTTPHEADER => array(
    "Authorization: Bearer rzg5h8gkybgzba8ykvkw9p==/1599144457846"
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```
{% endtab %}

{% tab title="Python" %}
```python
import requests

url = "https://api.saino.io/api/apis/email/upload-attachment"

payload = {}
files = [
  ('file', open('/path-to-file','rb'))
]
headers = {
  'Authorization': 'Bearer nhrk67bizz0qce1599144457846',
}

response = requests.request("POST", url, headers=headers, data = payload, files = files)

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
  curl_easy_setopt(curl, CURLOPT_URL, "https://api.saino.io/api/apis/email/upload-attachment");
  curl_easy_setopt(curl, CURLOPT_FOLLOWLOCATION, 1L);
  curl_easy_setopt(curl, CURLOPT_DEFAULT_PROTOCOL, "https");
  struct curl_slist *headers = NULL;
  headers = curl_slist_append(headers, "Authorization: Bearer 808ciij4p18351ymliiznhrk599144457846");
  curl_easy_setopt(curl, CURLOPT_HTTPHEADER, headers);
  curl_mime *mime;
  curl_mimepart *part;
  mime = curl_mime_init(curl);
  part = curl_mime_addpart(mime);
  curl_mime_name(part, "file");
  curl_mime_filedata(part, "/path-to-file");
  curl_easy_setopt(curl, CURLOPT_MIMEPOST, mime);
  res = curl_easy_perform(curl);
  curl_mime_free(mime);
}
curl_easy_cleanup(curl);

```
{% endtab %}

{% tab title="C\#" %}
```csharp
var client = new RestClient("https://api.saino.io/api/apis/email/upload-attachment");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("Authorization", "Bearer ymlipitzkg67bizz0qce1599144457846");
request.AddFile("file", "/path-to-file");
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```
{% endtab %}

{% tab title="HTTP" %}
```http
POST /api/apis/email/upload-attachment HTTP/1.1
Host: api.saino.io
Authorization: Bearer hrkv9rzg5hpitzkg67bizz0qce1599144457846
Cookie: Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW

----WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="file"; filename="tets.csv"
Content-Type: text/csv

(data)
----WebKitFormBoundary7MA4YWxkTrZu0gW

```
{% endtab %}

{% tab title="JAVA" %}
```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
  
MediaType mediaType = MediaType.parse("text/plain");

RequestBody body = new MultipartBody.Builder().setType(MultipartBody.FORM)
  .addFormDataPart("file","tets.csv",
    RequestBody.create(MediaType.parse("application/octet-stream"),
    new File("/path-to-file")))
  .build();
  
Request request = new Request.Builder()
  .url("https://api.saino.io/api/apis/email/upload-attachment")
  .method("POST", body)
  .addHeader("Authorization", "Bearer iznhrkv9rzg5h8gkybgzba8ykvqce1599144457846")
  .addHeader("Cookie", "__cfduid=df667dc82cf64d09c75ae34d29e9053bb1598528453")
  .build();
  
Response response = client.newCall(request).execute();
```
{% endtab %}

{% tab title="SWIFT" %}
```swift
import Foundation

var semaphore = DispatchSemaphore (value: 0)

let parameters = [
  [
    "key": "file",
    "src": "/path-to-file",
    "type": "file"
  ]] as [[String : Any]]

let boundary = "Boundary-\(UUID().uuidString)"
var body = ""
var error: Error? = nil
for param in parameters {
  if param["disabled"] == nil {
    let paramName = param["key"]!
    body += "--\(boundary)\r\n"
    body += "Content-Disposition:form-data; name=\"\(paramName)\""
    let paramType = param["type"] as! String
    if paramType == "text" {
      let paramValue = param["value"] as! String
      body += "\r\n\r\n\(paramValue)\r\n"
    } else {
      let paramSrc = param["src"] as! String
      let fileData = try NSData(contentsOfFile:paramSrc, options:[]) as Data
      let fileContent = String(data: fileData, encoding: .utf8)!
      body += "; filename=\"\(paramSrc)\"\r\n"
        + "Content-Type: \"content-type header\"\r\n\r\n\(fileContent)\r\n"
    }
  }
}
body += "--\(boundary)--\r\n";
let postData = body.data(using: .utf8)

var request = URLRequest(url: URL(string: "https://api.saino.io/api/apis/email/upload-attachment")!,timeoutInterval: Double.infinity)
request.addValue("Bearer 808ciij4pitzkg67bizz0qce1599144457846", forHTTPHeaderField: "Authorization")
request.addValue("multipart/form-data; boundary=\(boundary)", forHTTPHeaderField: "Content-Type")

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

