# Confidential SMS

Being the most trusted Communication Service provider by our banking domain-based clients, the team at [Saino](https://saino.io/) identified that the SMSes sent by these clients often include Confidential Details of their prestigious customers like OTPs, Transaction Notifications, etc. These details may sometimes be too critical to be stored/persisted into the systems.

So we came up with a solution that we would simply not store these details in our systems once it is sent to the operator for the delivery. However, we cannot promise a similar behavior from the Operators' side as it is not in our hands. This feature lets you make sure that your customers' confidential details are no longer persisted at least in our systems and assures better privacy to their data. 

{% hint style="info" %}
**T**his feature may sound exciting for some, it has one downside as well. Enabling this feature will not let you see the actual SMS content on Saino portal sections including reports, downloads, or any other place from our portal.
{% endhint %}

### **So how can you use this feature?**

Currently, it's possible to set a flag in the existing SMS API request and it's already documented in our [API documentation](https://apidocs.saino.io/sms-api/send-sms#optional-parameters). ****

You need to pass this parameter in the API request:  **&is\_confidential=1**

This is an **OPTIONAL** feature. Existing API requests will have no impact and will be working normally. Soon we will be adding this feature to our Web Application Portal too.  
  
Please feel free to reach out to our support team for any further clarifications or details on this.

