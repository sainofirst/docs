# Send SMS

To make it simple, We have designed a method which allows you to **send SMS in a single line** of the HTTP **GET** request:

```http
https://api.saino.io/api/apis/bulk-sms?token=enterAPI&senderid=YourApprovedSenderID&route=EnterRoute&number=EnterNumber&message=hello
```

This is all you need to send a message. No codings skills required, to test this, You can even send this message through your web browser address bar, Just copy the URL and change the parameters.  Now, this is something that you could put into your application without writing any code!

### Placeholder

Placeholder names will be provided by the application system from which you want to send messages. What you need to understand is where to put these placeholders. Let’s break down our example request in several lines so we can understand it closely:

```http
https://api.saino.io/api/apis/bulk-sms?
token=EnterAPIkey 
&senderid=YourApprovedSenderID
&route=EnterRouteName ( Transactional, Global, Promotional )
&number=EnterNumber ( Where SMS needs to be send )
&message=hello ( Enter your text message )
```

{% hint style="info" %}
If you want to send sms via user ID and password, That will replace token \(API key \) to below parameters :

username=myUsername&password=myPassword 

Remaining all parameters will be same
{% endhint %}

### Mandatory Parameters 

| Type | Parameter | Description |
| :--- | :--- | :--- |
| Token  | token= | Generate your API key at your Saino First account |
| Sender ID | &senderid= | The registered and approved Sender name |
| Route  | &route= | Type of connectivity like Global, Promotional, Transactional  |
| Number  | &number= | Number with country prefix. \(multiple numbers can be separated by comma.\) |
| Message  | &message= | Content of message |

### Optional Parameters

You can add these parameters in the HTTP API only, as per your requirement you can use one of them or all.   

| Type | Parameter | Description |
| :--- | :--- | :--- |
| DLT TemplateId | &dltTemplateId= | Only for India, If you want to pass directly template id via API you can do that with this parameter, Update Entity id directly under Saino app profile section. For more info click here - [https://help.saino.io/registration-on-dlt-india\#how-to-add-template-on-saino-platform](https://www.google.com/url?q=https://help.saino.io/registration-on-dlt-india%23how-to-add-template-on-saino-platform&sa=D&source=hangouts&ust=1615122091604000&usg=AFQjCNGF5QcEDit0MZuuvapjGx0l_WtsFw) |
| Unicode | &unicode=1 | Message can be send in any language \( Values 1 or 0 \) |
| Schedule | &time= | Schedule time \(in format i.e,yyyy-mm-dd hh:mm:ss\) at which the SMS has to be sent |
| Flash  | &flash=1 | Send flash sms via API \( Values 1 or 0 \) |
| Confidential SMS | &is\_confidential=1 | Saino Platform will not store the message. It will simply pass the actual content to the operator. More information click here |

### Got stuck?  <a id="got-stuck"></a>

No problem, we are here for you! We have the best support team available you around the clock, so just drop an email at support@saino.io

