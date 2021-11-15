---
description: >-
  The Sentiment API returns social insights such as likes, impressions,
  sentiment, and user posted comments (mentions) on social media sources such as
  Reddit, Twitter, & Stocktwits.
---

# 😀 Social

All **GET methods** are associated with retrieving Utradea's social insights by ticker(s)

```
// GET SENTIMENT
https://cloud.utradea.com/v1/get-social
```

{% hint style="info" %}
You must **pass the required headers** with your enterprise access token.

Expand the below GET method table for details.
{% endhint %}

### Endpoints

{% swagger method="get" path="https://cloud.utradea.com/v1/get-social" baseUrl="URL:" summary="/get-social" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" required="true" name="ticker" type="String" %}
ticker representing either a company or crypto currency.



**Accepted Values:**

`?ticker=PLTR`

`?ticker=PLTR,GOOGL`
{% endswagger-parameter %}

{% swagger-parameter in="query" required="true" name="social" type="String" %}
Indicator to include tickers that are trending as captured in the Social Dashboard.



**Accepted Values:**

`?social=reddit`

`?social=stocktwits`

`?social=twitter`

`?social=reddit,stocktwits,twitter`
{% endswagger-parameter %}

{% swagger-parameter in="query" name="charts" type="String" required="true" %}
The charts parameter defines the type of social insight that can be returned in this query. You can specify one type of chart or multiple charts.



**Accepted Values:**

`?charts=posts`,

`?charts=comments`,

`?charts=likes`,

`?charts=impressions`
{% endswagger-parameter %}

{% swagger-parameter in="header" required="true" name="Content-Type" type="String" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" required="true" name="Authorization" type="String" %}
${YOUR_APIKEY}
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful requests will return the following response." %}
```javascript
{ 
  statusCode: 200, 
  output: 
    [
      {
        "stocktwitsPosts": 1,
        "stocktwitsComments": 15,
        "stocktwitsLikes": 72,
        "stocktwitsImpressions": 3,
        "symbol": "PLTR",
        "timestamp": "2021-11-07T22:00:00.000Z"
      },
      {
        "stocktwitsPosts": 2,
        "stocktwitsComments": 0,
        "stocktwitsLikes": 0,
        "stocktwitsImpressions": 378,
        "symbol": "PLTR",
        "timestamp": "2021-11-07T22:15:00.000Z"
      },
      {
        "stocktwitsPosts": 2,
        "stocktwitsComments": 0,
        "stocktwitsLikes": 0,
        "stocktwitsImpressions": 166,
        "symbol": "PLTR",
        "timestamp": "2021-11-07T22:30:00.000Z"
      }
  ]
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="The following error message is triggered if you do not pass the proper query parameters." %}
```javascript
{
    statusCode: 400,
    errorMessage: "Invalid Chart Type Error."
}
```
{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="The following error message is triggered if you do not have the proper authentication." %}
```javascript
{
    statusCode: 403,
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
// Some code
const axios = require("axios")

const getIdeas = async () => new Promise((resolve, reject) => {
    var options = {
        method: 'GET',
        url: 'https://api.utradea.com/v1/get-social?ticker=PLTR',
        headers: {'
            'Content-Type': 'application/json',
            'Authorization': ${YOUR_APIKEY}
        
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

{% tab title="Response | Reddit" %}
```javascript
[
  {
    "redditPosts": 0,
    "redditComments": 0,
    "redditLikes": 0,
    "redditImpressions": 0,
    "symbol": "PLTR",
    "timestamp": "2021-11-07T21:00:00.000Z"
  },
  {
    "redditPosts": 0,
    "redditComments": 0,
    "redditLikes": 0,
    "redditImpressions": 0,
    "symbol": "PLTR",
    "timestamp": "2021-11-07T21:15:00.000Z"
  },
  {
    "redditPosts": 0,
    "redditComments": 0,
    "redditLikes": 0,
    "redditImpressions": 0,
    "symbol": "PLTR",
    "timestamp": "2021-11-07T21:30:00.000Z"
  }
]
```


{% endtab %}

{% tab title="Response | Twitter" %}
```javascript
[
  {
    "twitterPosts": 0,
    "twitterComments": 0,
    "twitterLikes": 0,
    "twitterImpressions": 0,
    "symbol": "PLTR",
    "timestamp": "2021-11-07T22:00:00.000Z"
  },
  {
    "twitterPosts": 0,
    "twitterComments": 0,
    "twitterLikes": 0,
    "twitterImpressions": 0,
    "symbol": "PLTR",
    "timestamp": "2021-11-07T22:15:00.000Z"
  },
  {
    "twitterPosts": 0,
    "twitterComments": 0,
    "twitterLikes": 0,
    "twitterImpressions": 0,
    "symbol": "PLTR",
    "timestamp": "2021-11-07T22:30:00.000Z"
  }
]
```
{% endtab %}

{% tab title="Response | Stocktwits" %}
```javascript
[
  {
    "stocktwitsPosts": 1,
    "stocktwitsComments": 15,
    "stocktwitsLikes": 72,
    "stocktwitsImpressions": 3,
    "symbol": "PLTR",
    "timestamp": "2021-11-07T22:00:00.000Z"
  },
  {
    "stocktwitsPosts": 2,
    "stocktwitsComments": 0,
    "stocktwitsLikes": 0,
    "stocktwitsImpressions": 378,
    "symbol": "PLTR",
    "timestamp": "2021-11-07T22:15:00.000Z"
  },
  {
    "stocktwitsPosts": 2,
    "stocktwitsComments": 0,
    "stocktwitsLikes": 0,
    "stocktwitsImpressions": 166,
    "symbol": "PLTR",
    "timestamp": "2021-11-07T22:30:00.000Z"
  }
]
```
{% endtab %}
{% endtabs %}

### Field Mappings

| Field Name  | Type    | Description                                                                                                                                                                    |
| ----------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| symbol      | String  | The company or cryptocurrency symbol.                                                                                                                                          |
| likes       | Integer | The number of likes made for a particular ticker at the recorded timestamp. This value is aggregated based on the specific social source, and aggregated at a point in time.   |
| posts       | Boolean | The number of posts made for a particular ticker at the recorded timestamp.This value is aggregated based on the specific social source, and aggregated at a point in time.    |
| comments    | Integer | The number of comments made for a particular ticker at the recorded timestamp.This value is aggregated based on the specific social source, and aggregated at a point in time. |
| impressions | Integer | The number of impressions made for a particular ticker at the recorded timestamp.                                                                                              |
| timestamp   | String  | The date and time associated with a recorded social insight. The timestamp is a string representation of a datetime object.                                                    |

