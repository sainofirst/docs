# Account & Balance Info

{% api-method method="get" host="<base\_url>" path="/my-account?token=<YOUR\_API\_TOKEN>" %}
{% api-method-summary %}
Check your account information balance
{% endapi-method-summary %}

{% api-method-description %}
Sometimes you may need to check your balance before sending any SMS, Voice Call or using any services provided by the SainoFirst  platform, use this API to do so.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="token" type="string" required=true %}
Your API token \(always keep it secret\)
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Account info successfully retrieved.
{% endapi-method-response-example-description %}

```javascript
{
  "status": true,
  "message": "Successfully Retrived Details.",
  "data": {
    "userId": <your_user_id>,
    "userRole": "<USER_ROLE_STRING>",
    "userName": "<USER_NMAE_STRING>",
    "emailId": "<EMAIL_ID_STRING>",
    "mobileNumber": "<MOBILE_NUMBER_STRING>",
    "contactDetails": {
      "clientName": "<CLIENT_NAME_STRING>",
      "companyName": "<COMPANY_NMAE_STRING>",
      "designation": "<DESIGNATION_STRING>",
      "address": "<ADDRESS_STRING>",
      "city": "<CITY_STRING>",
      "country": "<COUNTRY_STRING>",
      "pincode": "<ZIPCODE_STRING>",
      "state": "<STATE_STRING>",
      "website": "<WEBSITE_STRING>",
      "faxNumber": <fax_number>,
      "taxNumber": "<TAX_NUMBER_OR_ID_STRING>"
    },
    "profile": {
      "language": "<USER_LANGUAGE_STRING>",
      "timezone": "<USER_TIMEZONE_STRING>",
      "currency": "USER_CURRENCY_STRING",
      "balance": <balance_decimal>
    },
    /* Apps allowed only for current API token (token passed in request url)
    *  will be shown here
    */
    "appsAvailable": [
      "BULK_SMS",
      "BULK_VOICE",
      "MISSED_CALL",
      "SHORT_CODE",
      "IVR_TOLL",
      "WHATSAPP",
      "SMPP"
    ]
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Could not find data.
{% endapi-method-response-example-description %}

```javascript
{
    status: false, 
    message: "No such user found." // Reason or Error Messgae.
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}
Something went wrong on our side while processing your request.
{% endapi-method-response-example-description %}

```javascript
{
    status: false, 
    message: "Unable to fetch account details." // Reason or Error Messgae.
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



