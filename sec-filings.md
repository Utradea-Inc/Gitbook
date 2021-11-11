---
description: The SEC API returns sec filings analyzed by Utradea.
---

# 📄 SEC Filings

```
// GET SEC
https://api.utradea.com/v1/get-sec
```

### Endpoints

{% swagger method="get" path="https://api.utradea.com/v1/get-sec" baseUrl="URL:" summary="/get-sec" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="ticker" type="String" required="true" %}
Pass a ticker symbol to return sec filings specific to that ticker.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="documentType" type="String" %}
Pass document type to filter on what type of sec filings to return. If this option is not passed the API will return what is available.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="startDate" type="String" %}
Pass an integer representation of a datetime object to specify the start date. If this option is not passed the API will query by the first available datetime stamp associated with a stored sec filing.



A**ccepted Values:**

20211103
{% endswagger-parameter %}

{% swagger-parameter in="query" name="endDate" type="String" %}
Pass an integer representation of a datetime object to specify the start date. If this option is not passed the API will return results up to the current date.



**Accepted Values:**

20211104
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
${YOUR_APIKEY}
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}

{% swagger-response status="429: Too Many Requests" description="" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Node.js" %}
```javascript
const axios = require("axios")

const getSEC = async () => new Promise((resolve, reject) => {
    var options = {
        method: 'GET',
        url: 'https://api.utradea.com/v1/get-sec?ticker=PLTR',
        headers: {'
            'Content-Type': 'application/json',
            'Authorization': ${YOUR_ENTERPRISE_ACCESS_TOKEN}
        }
    }
    axios.request(options)
        .then(function (response) {
            resolve(response.data);
        }).catch(function (error) {
            console.log('Error on Fetch: ' + error.message);
            reject(error);
        });
});
```
{% endtab %}

{% tab title="Sample JSON Response" %}
```javascript
{
    "endpoint": "https://api.utradea.com/enterprise/get-sec",
    "data": [
            {
                'ticker': "PLTR",
                'cik'   : "123356",
                'company': "Palantir Technologies",
                'filings': {
                    '10-K': [
                        {
                            'accessionNumber': "",
                            'documentLink':    "",
                            'itemNumbers':     "",
                            'items':           "",
                            'articleContent': {
                                    'summary': "",
                                    'articleDetails': [],
                                    'articleNumberReferences': [],
                                    'exhibits':[]
                            },
                            'acceptedDate': 2020-06-05T00:45:15.000+00:00,
                        }
                    ],
                    '10-Q': [
                         {
                            'accessionNumber': "",
                            'documentLink':    "",
                            'itemNumbers':     "",
                            'items':           "",
                            'articleContent': {
                                    'summary': "",
                                    'articleDetails': [],
                                    'articleNumberReferences': [],
                                    'exhibits':[]
                            },
                            'acceptedDate': 2020-06-05T00:45:15.000+00:00,
                        }
                    ],
                    '8-K' : [
                         {
                            'accessionNumber': "",
                            'documentLink':    "",
                            'itemNumbers':     "",
                            'items':           "",
                            'articleContent': {
                                    'summary': "",
                                    'articleDetails': [],
                                    'articleNumberReferences': [],
                                    'exhibits':[]
                            },
                            'acceptedDate': 2020-06-05T00:45:15.000+00:00,
                        }
                    ],
                }
            }
    ]
}
```
{% endtab %}
{% endtabs %}

### Field Mappings

|                                  | Type             | Description                                                                                                                                                                                                                                                                                                                                     |
| -------------------------------- | ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ticker                           | String           | The company or cryptocurrency symbol.                                                                                                                                                                                                                                                                                                           |
| documentType                     | String           | <p>An identifier for the type of sec filing offered in the API.</p><p></p><p>Accepted Values:</p><p>"<code>8-K</code>"</p><p>"<code>8-K/A</code>"</p><p><code>"10-K"</code></p><p><code>"10-K/A"</code></p><p><code>"10-Q"</code></p><p><code>"10-Q/A"</code></p><p><code>"6-K"</code></p><p><code>"6-K/A"</code></p><p><code>"20-F"</code></p> |
| accessionNumber                  | String           | The unique identifier for the sec document filing.                                                                                                                                                                                                                                                                                              |
| exhibits                         | Array            | The exhibits are attached files & data associated to an SEC filing.                                                                                                                                                                                                                                                                             |
| articleContent                   | Object           | This is a object that saves the summarized results from Utradea's analytics.                                                                                                                                                                                                                                                                    |
| articleContent \| summary        | Object \| String | <p>This field is the summary field, providing a brief description of the filing. </p><p>If there is no summary, then it will default to "Please view the filing in detail..."</p>                                                                                                                                                               |
| articleContent \| articleAmounts | Object \| Array  | This list represents all number/digit/percent references captured in the sec filing.                                                                                                                                                                                                                                                            |
| articleContent \| articleDetails | Object \| Array  | This list represents important organization mentions, dates, and keyword phrases captured in the sec filing.                                                                                                                                                                                                                                    |
| documentLink                     | String           | This is the URL for the original sec filing in html format.                                                                                                                                                                                                                                                                                     |





