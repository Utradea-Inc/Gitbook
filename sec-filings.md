---
description: The SEC API returns sec filings analyzed by Utradea.
---

# 📄 SEC Filings

```
// GET SEC
https://cloud.utradea.com/v1/get-sec
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

{% swagger-response status="200: OK" description="Successful requests will return the following response." %}
```javascript
{
    // Response
    statusCode: 200,
    output: [
  {
    "documentLink": "https://www.sec.gov/Archives/edgar/data/1820852/000114036121037701/brhc10030482_10q.htm",
    "acceptedDate": "2021-11-12T22:23:32.000Z",
    "articleContent": {
      "summary": "On August 19, 2021, the Company issued an unsecured promissory note (the “Promissory Note”) to the Sponsor, pursuant to which the Company could borrow up to an aggregate principal amount of $2,000,000. The Promissory Note is non-interest bearing and payable on the consummation of the merger, capital stock exchange, asset acquisition,\n              stock purchase, reorganization or similar business combination with one or more businesses. Once the warrants become exercisable, the Company may redeem the Public Warrants: The amount outstanding under the Promissory Note  ",
      "articleDetails": [
        "an aggregate principal amount",
        "the Promissory Note",
        "which",
        "the consummation",
        "the merger",
        "one or more businesses",
        "the Sponsor"
      ],
      "articleNumberReferences": [
        "$2,000,000"
      ],
      "exhibits": [
        "https://www.sec.gov/Archives/edgar/data/1820852/000114036121037701/brhc10030482_ex31-1.htm",
        "https://www.sec.gov/Archives/edgar/data/1820852/000114036121037701/brhc10030482_ex31-2.htm",
        "https://www.sec.gov/Archives/edgar/data/1820852/000114036121037701/brhc10030482_ex32-1.htm",
        "https://www.sec.gov/Archives/edgar/data/1820852/000114036121037701/brhc10030482_ex32-2.htm"
      ]
    },
    "company": "Sports Entertainment Acquisition Corp.",
    "documentType": "10-Q",
    "items": [],
    "ticker": "SEAH"
  }
]
}
```
{% endswagger-response %}

{% swagger-response status="400" description="The following error message is triggered if you do not pass the proper query parameters." %}
```javascript
{
    statusCode: 400,
    errorMessage: "Invalid Chart Type Error."
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="The following error message is triggered if you do not have the proper authentication." %}
```javascript
{
    statusCode: 401,
    errorMessage: "Invalid Chart Type Error."
}
```
{% endswagger-response %}

{% swagger-response status="429: Too Many Requests" description="The following error message is triggered when the number of requests exceed the rate limit specified for your membership tier." %}
```javascript
{
    statusCode: 429,
    errorMessage: "You have exceeded your rate limit of 5 requests in 15 minutes!"
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="The following error message is triggered if there is an issue with Utradea's server." %}
```javascript
{
    statusCode: 500,
    errorMessage: "Internal Server Error."
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
[
  {
    "documentLink": "https://www.sec.gov/Archives/edgar/data/1820852/000114036121037701/brhc10030482_10q.htm",
    "acceptedDate": "2021-11-12T22:23:32.000Z",
    "articleContent": {
      "summary": "On August 19, 2021, the Company issued an unsecured promissory note (the “Promissory Note”) to the Sponsor, pursuant to which the Company could borrow up to an aggregate principal amount of $2,000,000. The Promissory Note is non-interest bearing and payable on the consummation of the merger, capital stock exchange, asset acquisition,\n              stock purchase, reorganization or similar business combination with one or more businesses. Once the warrants become exercisable, the Company may redeem the Public Warrants: The amount outstanding under the Promissory Note  ",
      "articleDetails": [
        "an aggregate principal amount",
        "the Promissory Note",
        "which",
        "the consummation",
        "the merger",
        "one or more businesses",
        "the Sponsor"
      ],
      "articleNumberReferences": [
        "$2,000,000"
      ],
      "exhibits": [
        "https://www.sec.gov/Archives/edgar/data/1820852/000114036121037701/brhc10030482_ex31-1.htm",
        "https://www.sec.gov/Archives/edgar/data/1820852/000114036121037701/brhc10030482_ex31-2.htm",
        "https://www.sec.gov/Archives/edgar/data/1820852/000114036121037701/brhc10030482_ex32-1.htm",
        "https://www.sec.gov/Archives/edgar/data/1820852/000114036121037701/brhc10030482_ex32-2.htm"
      ]
    },
    "company": "Sports Entertainment Acquisition Corp.",
    "documentType": "10-Q",
    "items": [],
    "ticker": "SEAH"
  }
]
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





