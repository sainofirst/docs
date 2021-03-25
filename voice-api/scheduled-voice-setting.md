# Scheduled Voice Setting

There are many cases where you might need to change the Scheduled Time of voice call which you had scheduled earlier. To do so, use this API.

{% api-method method="put" host="<base\_url>" path="/bulk-voice/reschedule" %}
{% api-method-summary %}
Reschedule \(Change\) the Schedule Date of Voice Call
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="voice\_id" type="integer" required=true %}
Unique ID which was received in **response** while sending the voice call.
{% endapi-method-parameter %}

{% api-method-parameter name="new\_send\_at" type="integer" required=true %}
Epoch Time \(time in milliseconds\) as like Voice Call **`send_at`** parameter.
{% endapi-method-parameter %}

{% api-method-parameter name="timezone" type="string" required=true %}
Timezone. Refer the Timezone Table for more information.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{    status: true,    message: "Voice call rescheduled successfully."}
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

### Example: Rescheduling/Changing the scheduled time of voice

A **`HTTP PUT`** request must have body in below format.

#### Request:

{% tabs %}
{% tab title="Rescheduled-Voice-Request.json" %}
```javascript
{    
"voice_id": XXX, // The Unique ID you got in response of Send-Voice call request.    
"new_send_at": 1569266700,    
"timezone": "Asia/Kolkata(GMT +05:30)" // timezone
}
```
{% endtab %}
{% endtabs %}

#### Response:

After the request is successfully received at our server, response will be like below with _**`Status Code: 200`**_

{% tabs %}
{% tab title="Rescheduled-Voice-Response.json" %}
```javascript
{    status: true,    message: "Voice call rescheduled successfully."}
```
{% endtab %}
{% endtabs %}



## Cancel Scheduled Voice Call

If you have scheduled a voice call for future date/time, but because of any reason you may want to cancel the call, before it is actually sent to the recipient. To do so, this API comes handy.  

{% api-method method="delete" host="<base\_url>" path="/bulk-voice/cancelScheduled/{voice\_id}" %}
{% api-method-summary %}
Cancel Scheduled Voice Call
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="voice\_id" type="number" required=true %}
**Unique ID** which was received in the **response** of Send Voice Call.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{    status: true,     message: "Voice call cancelled successfully."}
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

### Example: Cancel/Delete The scheduled Voice Call

A **`HTTP DELTE`** request must have URL in below format.

#### Request URL:

{% tabs %}
{% tab title="" %}
```java
https://<base_url>/bulk-voice/cancelScheduled/207 
```
{% endtab %}
{% endtabs %}

{% hint style="success" %}
here, _**`207`**_ is the Unique ID of Send Voice Call Request.
{% endhint %}

#### Response:

After the request is successfully received at our server, response will be like below with _**`Status Code: 200`**_

{% tabs %}
{% tab title="Cancel-Scheduled-Voice-Response.json" %}
```javascript
{    status: true,    message: "Voice call cancelled successfully."}
```
{% endtab %}
{% endtabs %}

