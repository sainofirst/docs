# Base URL Setting

Before you start using [SainoFirst](https://sainofirst.com) Platform's API, you should consider reading the API documentations thoroughly. Although, we have kept everything simple for the ease of integration of your application with our platform, but still there are some steps need to be followed to have seamless integration. 

## Base URL for our platform's APIs

| Base URL |  Description |
| :--- | :--- |
| **`https://api.saino.io/api/apis`** | Use this as base path for all the API endpoints available on [SainoFirst](https://sainofirst.com) Platform. |

## Authentication Methods

You can use **any ONE** of the authentication methods from below.

### 1. Passing API Token in Request Header _\(Recommended\)_

{% hint style="success" %}
Each request is validated by looking for valid API token into the Header of the HTTP request.
{% endhint %}

| Header Name \(or Header Key\) | Value |
| :--- | :--- |
| **`Authorization`** | **`YOUR_API_TOKEN`** |

### 2. Passing API Token in Query Parameter _**\(Deprecated, will be removed in future\)**_

<table>
  <thead>
    <tr>
      <th style="text-align:left">Authentication</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Query Parameter Name : <b><code>token</code></b>
      </td>
      <td style="text-align:left">
        <p>Every API request URL must add <code>?token=&lt;YOUR_API_TOKEN&gt;</code> in
          the URL path.</p>
        <p></p>
        <p>This is applicable for all HTTP method calls.</p>
      </td>
    </tr>
  </tbody>
</table>

{% hint style="warning" %}
### IMPORTANT:

For each API request, you have to put a query parameter named **`token`** with value as **`<YOUR_API_TOKEN>.`**

**Pattern: `<base_url>/path?token=<YOUR_API_TOKEN>&otherParam=...`**

Example: To get your account information, the complete URL will be...  
 _**GET Method:**_   `https://api.saino.io/api/apis/my-account?token=<API_TOKEN>`
{% endhint %}

### 



