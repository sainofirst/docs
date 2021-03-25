# Send Voice Call

Sending a Voice call is completely different from Sending Text SMS. A Voice call involves multiple factor to be considered **before** & **after** the Voice Call is sent. But not to worry when you are using [SainoFirst](https://sainofirst.com)'s Voice Platform. We've taken all complexities on us, so that you can have a seamless integration.  
  
To send voice call you have below options:-

1. **Text-To-Speech** based Voice Call
2. **Pre-Recorded Audio File** based voice Call

{% api-method method="post" host="<base\_url>" path="/bulk-voice" %}
{% api-method-summary %}
Voice Call Send
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="reportUrl" type="string" required=false %}
The URL at which Voice Campaign reports will be sent for this campaign.   
  
_Read Reports & Deliveries section below for more information_
{% endapi-method-parameter %}

{% api-method-parameter name="text" type="string" required=false %}
The actual text that would be converted to voice by Text-to-Speech synthesis and will be played over Voice call.  
  
🚩**Required** if **is\_text** is **`true`**  
✔  **Not-Required** if **is\_text** is **`false`**
{% endapi-method-parameter %}

{% api-method-parameter name="audio\_file\_url" type="string" required=false %}
URL of audio file that will be played on voice call.  
  
🚩 Make sure the above URL passed, is publicly accessible. If call scheduled for future date, this URL must be accessible till the date call is scheduled at.
{% endapi-method-parameter %}

{% api-method-parameter name="config" type="object" required=false %}
See below for more details on `config` object. There is a separate section with detailed explanation.
{% endapi-method-parameter %}

{% api-method-parameter name="timezone" type="string" required=false %}
Timezone. See the timezone table for more help.   
  
 📌 **Required** if `send_at` is passed in the request.
{% endapi-method-parameter %}

{% api-method-parameter name="send\_at" type="integer" required=false %}
Epoch time \(time in milliseconds\) equivalent to the **Actual Future Time** \(at which the call must be sent\).   
  
_1. Time must be in future. \(Min. 5 minutes, Max. 60 Days\)  
2. All the requests with past date/time will be rejected.  
3. All the request with future date more than 60 days, will be rejected._
{% endapi-method-parameter %}

{% api-method-parameter name="subscription\_id" type="integer" required=true %}
Pricing and Routes will be based on this ID. The value of this ID can be accessed from the SainoFirst's Application under connectivity. If subscription not assigned please contact your account manager. 
{% endapi-method-parameter %}

{% api-method-parameter name="maxLengthOfCall" type="number" required=true %}
Limits the call duration to this much seconds, the call will be disconnected after this much second automatically even if receiver is not cutting the call.   
\(Value In Second\)  
  
📌 This max duration is not applicable for the calls which are forwarded by the receiver.
{% endapi-method-parameter %}

{% api-method-parameter name="speech\_rate" type="number" required=false %}
minimum 0.5 - maximum 2 \(Lower the value, Slower the speed of voice audio converted via text-to-speech synthesis \)  
  
🚩 **Required** if **is\_text** is **`true`**  
✔   **Not-Required** if **is\_text** is **`false`**
{% endapi-method-parameter %}

{% api-method-parameter name="language\_id" type="integer" required=false %}
Language ID of the text to be converted via Text-to-Speech synthesis. Please refer voice call language page.  
  
🚩 **Required** if **is\_text** is **`true`**  
✔   **Not-Required** if **is\_text** is **`false`**
{% endapi-method-parameter %}

{% api-method-parameter name="is\_text" type="boolean" required=true %}
Set this to **`true`** for sending _**text-to-speech**_ based voice call.  
  
Set this to **`false`** for sending _**pre-recorded audio**_ based voice call.  
  
If **false** : _**`audio_file_url`**_ parameter is mandatory.
{% endapi-method-parameter %}

{% api-method-parameter name="numbers" type="array" required=true %}
Array of `String` of numbers.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{    "id":xxx, // permanent ID of current request    "status":true,    "message":"Voice Call Sent/scheduled Successfully."}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{    "status":false,    "message":"Information about why the request is rejected (in string format)"}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{    "status":false,    "message":"Auth-Error root cause will be stated here."}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{    "status":false,    "message":"Forbidded Resource Access."}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{    "status":false,    "message":"Something Went Wrong"}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Simple Text-To-Speech Voice Call \( 2 Factor Authentication \)

#### Request:

A `HTTP POST` request should contain body like below.

{% tabs %}
{% tab title="Text-to-Speech-Voice-Call-Request.json" %}
```javascript
{
    "numbers": [        
             "xxxxxxxxxx"    
        ], // if same message is to be sent on multiple numbers, just add them into this array    
    "text": "This is text-to-speech service.",    
    "language_id": 4, // Language Id of Text    
    "maxLengthOfCall": 30, // Maximum Length of call, in seconds    
    "subscription_id": 5, // Subscription used (for Price calculation and Routing)    
    "speech_rate": 1, // Speed of voice call (lower the value, slower the speed [0.5 to 2])    
    "is_text": true,
    // The url at which you want to track the delivery report for this campaign
    "reportUrl": "https://app.sainofirst.com/api-delivery-endpoint?customKey1=CustomValue1&customKey2=CustomValue2"
}
```
{% endtab %}
{% endtabs %}

#### Response:

After the request is successfully received at our server, response will be like below with _**`Status Code: 200`**_

{% tabs %}
{% tab title="Response.json" %}
```javascript
{    
    "status":true,    
    "message":"Voice Call scheduled Successfully.",
    "id":xyz // request-id for this request, can be used for future references.
}
```
{% endtab %}
{% endtabs %}

### Fully Featured Text-To-Speech Voice Call

#### Request:

A `HTTP POST` request should contain body like below.

{% tabs %}
{% tab title="Text-to-Speech-Voice-Call-Request.json" %}
```javascript
{
    "numbers": [ "xxxxxxxxxx" ], // if same message is to be sent on multiple numbers, just add then in this array like this    
    "text": "This is text-to-speech service.",    
    "language_id": 4, // Language Id of Text    
    "maxLengthOfCall": 30, // Maximum Length of call, in seconds    
    "subscription_id": 5, // Subscription used (for Price calculation and Routing)    
    "speech_rate": 1, // Speed of voice call (lower the value, slower the speed [0.5 to 2])    
    "is_text": true, 
    "config": { // optional        
        "repeat": 1, // If pressed, voice message will be repeated (maxLengthOfCall will be counted)        
        "callTransfer": {            
                "transferKey": 2, // While call is active, pressing this key will forward the call            
                "transferNumber": xxxxxxxxxx // Forward call to this Number         
            }    
        },    
    "send_at": 1569266700, // required if scheduled for later date or time, otherwise optional    
    "timezone": "Asia/Kolkata(GMT +05:30)" // timezone,
    // The url at which you want to track the delivery report for this campaign
    "reportUrl": "https://app.sainofirst.com/api-delivery-endpoint?customKey1=CustomValue1&customKey2=CustomValue2"
}
```
{% endtab %}
{% endtabs %}

#### Response:

After the request is successfully received at our server, response will be like below with _**`Status Code: 200`**_

{% tabs %}
{% tab title="Response.json" %}
```javascript
{
    "status":true,    
    "message":"Voice Call scheduled Successfully.",     
    "id":xyz // request-id for this request, can be used for future references.
}
```
{% endtab %}
{% endtabs %}

### Pre-Recorded Audio Voice Call

#### Request: 

A `HTTP POST` request should contain body like below.

{% tabs %}
{% tab title="Pre-Recorded-Voice-Call-Request.json" %}
```javascript
{    
    "numbers": [        "xxxxxxxxxx"    ], // if same message is to be sent on multiple numbers, just add then in this array like this    
    "maxLengthOfCall": 30, // Maximum Length of call, in seconds    
    "subscription_id": 5, // Subscription used (for Price calculation and Routing)    
    "is_text": false,    
    "audio_file_url": "https://somefancy-audio-file-url", // required, is_text is true    
    "config": { // optional        
        "repeat": 1, // If pressed, voice message will be repeated (maxLengthOfCall will be counted)        
        "callTransfer": {            
            "transferKey": 2, // While call is active, pressing this key will forward the call            
            "transferNumber": xxxxxxxxxx // Forward call to this Number         
        }    
    },    
    "send_at": 1569266700, // required if scheduled for later date or time, otherwise optional    
    "timezone": "Asia/Kolkata(GMT +05:30)", // timezone
    // The url at which you want to track the delivery report for this campaign
      "reportUrl": "https://app.sainofirst.com/api-delivery-endpoint?customKey1=CustomValue1&customKey2=CustomValue2"
}
```
{% endtab %}
{% endtabs %}

#### Response:

After the request is successfully received at our server, response will be like below with _**`Status Code: 200`**_

{% tabs %}
{% tab title="Response.json" %}
```javascript
{
    "status":true,
    "message":"Voice Call scheduled Successfully.",     
    "id":xyz // request-id for this request, can be used for future references.
}
```
{% endtab %}
{% endtabs %}

## Advanced Voice Call:   How to _**Configure**_ Voice Call ?

_Advanced voice call_  is the voice call where Listener \(or Receiver\) will be able to interact even with the simple **pre-recorded** or **text-to-speech** voice call.  
  
**Features in Advance voice call:**  

* Repeat the same voice message again on press of 'Assigned' key.
* Forward the call to some other \(predefined\) number on press of 'Assigned' key.
* Capture the response of every phone key pressed by the user while the call is going on.

The `config` parameter of the request body is used to make a advanced voice call.

This parameter is a **JSON** Object which has two properties.

1. `repeat` -  Value must be a single digit number. On press of this number key, the call will be repeated.
2. `callTransfer` - Value is an object with two properties:                                     `transferKey` -  Value must be a single digit number. On press of this number key, the call will be repeated.

<table>
  <thead>
    <tr>
      <th style="text-align:center">Parameter</th>
      <th style="text-align:center">Value Type</th>
      <th style="text-align:center">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:center"><code>repeat</code>
      </td>
      <td style="text-align:center">Single Digit Number</td>
      <td style="text-align:center">
        <p></p>
        <p>On press of this number key, the call will be repeated.</p>
        <p></p>
        <p><em>The vice call will be disconnected automatically when the <code>maxLengthOfCall</code> is reached.</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:center"><code>callTransfer</code>
      </td>
      <td style="text-align:center">Object</td>
      <td style="text-align:center">
        <p>Must contain two properties inside this object.</p>
        <p></p>
        <ol>
          <li><code>transferKey</code> - On press of this key, call will be forwarded.</li>
          <li><code>transferNumber</code> - Number on which call to be forwarded.</li>
        </ol>
      </td>
    </tr>
  </tbody>
</table>

Example:-

{% tabs %}
{% tab title="Advanced-Voice-Config-PART.json" %}
```javascript
"config": { // optional        
    "repeat": 1, // If pressed, voice message will be repeated (maxLengthOfCall will be counted)        
    "callTransfer": {            
    "transferKey": 2, // While call is active, pressing this key will forward the call            
    "transferNumber": xxxxxxxxxx // Forward call to this Number         
    }    
},
```
{% endtab %}
{% endtabs %}

### Reports & Deliveries

In order to get delivery reports directly into your system you need to take care of few simple things.

* Please make sure that, the URL passed in the field `reportUrl`, **must accept** **`HTTP POST`** request with **`JSON`** request body.
* If you wish to get any additional data in the report callback, you should user query parameters and values in the URL itself. 

{% hint style="info" %}
If you don't pass the `reportUrl` parameter in request body, we will not be able to push the reports to your system. However, messages will still be delivered to the destination.
{% endhint %}

