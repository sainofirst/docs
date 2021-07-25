---
description: HTTP Post API to send SMS.
---

# Send SMS \(POST API\)

{% api-method method="post" host="<base\_url>" path="/bulk-sms" %}
{% api-method-summary %}
Send SMS
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to send SMS.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Your API key in request header.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="is\_confidential" type="boolean" required=false %}
0 - Send as Normal SMS  
1 - Send as Confidential SMS  
  
Read more on What is Confidential SMS?
{% endapi-method-parameter %}

{% api-method-parameter name="dltTemplateId" type="number" required=false %}
Only for India, If you want to pass directly template id via API you can do that with this parameter., update Entity under Saino app profile section. For more info open below link - https://help.saino.io/registration-on-dlt-india\#how-to-add-template-on-saino-platform
{% endapi-method-parameter %}

{% api-method-parameter name="reportUrl" type="string" required=false %}
The URL at which the SMS reports will be sent for this campaign.   
  
_Read Reports & Deliveries section below for more information._
{% endapi-method-parameter %}

{% api-method-parameter name="senderid" type="string" required=true %}
The registered and approved Sender name.
{% endapi-method-parameter %}

{% api-method-parameter name="route" type="string" required=true %}
Type of connectivity ex Global, Promotional, Transactional, etc.
{% endapi-method-parameter %}

{% api-method-parameter name="number" type="string" required=true %}
Number with country prefix. \(multiple numbers can be separated by comma.\)
{% endapi-method-parameter %}

{% api-method-parameter name="message" type="string" required=true %}
SMS text body. The actual message.
{% endapi-method-parameter %}

{% api-method-parameter name="unicode" type="number" required=false %}
Message can be send in any language \( Values 1 or 0 \)
{% endapi-method-parameter %}

{% api-method-parameter name="time" type="string" required=false %}
Schedule time \(in format i.e, yyyy-mm-dd hh:mm:ss\) at which the SMS has to be sent
{% endapi-method-parameter %}

{% api-method-parameter name="flash" type="number" required=false %}
Send flash SMS via API \( Values 1 or 0 \)
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
SMS sent successfully.  
  
**campaignId** : This ID is the reference ID of your request. You can store this ID to capture the deliveries specific to this campaign.  For every request, you will get a new and unique _campaignId._
{% endapi-method-response-example-description %}

```javascript
{
    status: true,
    data: {
        campaignId: 12345
      },
    message: "SMS Sent Successfully."
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Error in request data.
{% endapi-method-response-example-description %}

```javascript
{
    status: false,
    message: "Error_Message_For_Root_Cause"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Reports & Deliveries

In order to get delivery reports directly into your system you need to take care of few simple things.

* Please make sure that, the URL passed in the field `reportUrl`, **must accept** **`HTTP POST`** request with **`JSON`** request body.
* If you wish to get any additional data in the report callback, you should user query parameters and values in the URL itself.

{% hint style="info" %}
If you don't pass the `reportUrl` parameter in request body, we will not be able to push the reports to your system. However, messages will still be delivered to the destination.
{% endhint %}

### Sample Request

{% tabs %}
{% tab title="Request Body" %}
```text
{
	"senderid": "SAIFST",
	"route": "Transactional",
	"number": 989XXXXXXX,
	"message": "Hello SainoFirst!! My first Post API.",
	
	// The url at which you want to track the delivery report for this campaign
  "reportUrl": "https://app.sainofirst.com/api-delivery-endpoint?customKey1=CustomValue1&customKey2=CustomValue2" 
}
```
{% endtab %}

{% tab title="Response Body" %}
```text
{
    "status": true,
    "data": {
        "campaignId": 12345 // this id should be preserved to track the sms reports.
    },
    "message": "SMS sent successfully."
}
```
{% endtab %}
{% endtabs %}



