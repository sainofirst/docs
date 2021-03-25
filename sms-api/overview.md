# Overview

[Saino First](https://sainofirst.com) makes sending and receiving SMS easy. Find the documentation, sample codes and developer tools you need to build exactly what you want, fast & secure. We’ll handle all the complexity of mobile operators and global regulations. Let’s get building.

Our SMS API allows you to send text messages to users around the globe through simple RESTful APIs.

## Quick check before using API

{% hint style="success" %}
#### HTTP Methods : For SMS api 

* **`GET`** – To send a GET request for sending SMS with data in request's query parameter.
* **`POST`** - To send a POST request for sending SMS with data in body of request.
{% endhint %}

### **Number Formatting** 

Numbers are important to understand when working with the API. The following points should be considered before developing the Application.

All phone numbers in the APIs use **E.164** format. It means that numbers:

* Omit both a leading + and the international code such as 00.
* Contain no special characters, such as  `' " / \  ,  ( ) blank space` etc.

{% hint style="info" %}
For example, **Indian numbers** have format like **91**_7777084093_. A **UK number** would have the format **44**_7700314144_     \(where, **91** & **44** are the country code\)  
{% endhint %}

{% hint style="success" %}
If you are using it for **India**, using**`Transactional`** or **`Promotional`** connectivity then the country code 91 is optional. 
{% endhint %}

### Routes or Connectivity

Saino First have multiple gateway but majorly below 3 routes are used for sending messages via API.

1. **Global**
2. **Transactional**
3. **Promotional**

**`Global`** gateway can be used to send messages to more than **190+ countries**. The API request **must** contain the numbers with country code, else the message will be failed.  

**`Promotional`** and **`Transactional`** connectivity is used only for India. If country code is not found, the **91** _\(country's default code\)_ will be appended before all mobile numbers automatically.

{% hint style="info" %}
Multiple country have different price for messages so the price will be deducted accordingly. The current price/message can be seen under **`Apps > SMS > Connectivity`**. 

Price calculations are done on the basis of **`Number of SMS * cost per SMS`**. 

Multi countries numbers can be send on one request. [Saino First](https://sainofirst.com) system will auto calculate based on number of messages.
{% endhint %}

### Sender ID

Global gateway have open Sender ID which can be approved based on requirement but in India sender id is mandatory. While sending a message you can use any approved sender IDs for your account.

In case you have not created a sender ID, you can always create one through our customer portal. It can be created under **`SMS App > Manage > Sender ID`**. Once the Sender ID is approved, you can start sending the messages.



### Message Template

Mostly we have open content but many countries have restrictions on content template. Before production, please test your content by sending a test message Otherwise, the _SMS may end up being rejected._



