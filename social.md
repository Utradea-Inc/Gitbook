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

{% swagger-parameter in="query" required="true" name="tickers" type="String" %}
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

{% tab title="Sample Response " %}
```javascript
[
  {
    "stocktwitsPosts": 98,
    "twitterPosts": 429,
    "redditPosts": 1,
    "stocktwitsComments": 161,
    "twitterComments": 17318,
    "redditComments": 21,
    "stocktwitsLikes": 554,
    "twitterLikes": 86789,
    "redditLikes": 18,
    "stocktwitsImpressions": 11897,
    "twitterImpressions": 526226,
    "redditImpressions": 0,
    "symbol": "AMC",
    "timestamp": "2021-11-14T21:00:00.000Z"
  },
  {
    "stocktwitsPosts": 96,
    "twitterPosts": 281,
    "redditPosts": 1,
    "stocktwitsComments": 197,
    "twitterComments": 32279,
    "redditComments": 0,
    "stocktwitsLikes": 781,
    "twitterLikes": 160733,
    "redditLikes": 0,
    "stocktwitsImpressions": 10257,
    "twitterImpressions": 541867,
    "redditImpressions": 0,
    "symbol": "AMC",
    "timestamp": "2021-11-14T22:00:00.000Z"
  },
  {
    "stocktwitsPosts": 105,
    "twitterPosts": 312,
    "redditPosts": 0,
    "stocktwitsComments": 127,
    "twitterComments": 27503,
    "redditComments": 0,
    "stocktwitsLikes": 766,
    "twitterLikes": 152436,
    "redditLikes": 0,
    "stocktwitsImpressions": 50234,
    "twitterImpressions": 416098,
    "redditImpressions": 0,
    "symbol": "AMC",
    "timestamp": "2021-11-14T23:00:00.000Z"
  },
  {
    "stocktwitsPosts": 0,
    "twitterPosts": 0,
    "redditPosts": 0,
    "stocktwitsComments": 77,
    "twitterComments": 14986,
    "redditComments": 0,
    "stocktwitsLikes": 487,
    "twitterLikes": 80375,
    "redditLikes": 0,
    "stocktwitsImpressions": 0,
    "twitterImpressions": 0,
    "redditImpressions": 0,
    "symbol": "AMC",
    "timestamp": "2021-11-15T00:00:00.000Z"
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

