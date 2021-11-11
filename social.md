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
https://api.utradea.com/v1/get-social
```

{% hint style="info" %}
You must **pass the required headers** with your enterprise access token.

Expand the below GET method table for details.
{% endhint %}

### Endpoints

{% swagger method="get" path="https://api.utradea.com/v1/get-social" baseUrl="URL:" summary="/get-social" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" required="true" name="ticker" type="String" %}
ticker representing either a company or crypto currency.



Accepted Values:

`?ticker='PLTR'`

`?ticker='PLTR,GOOGL'`
{% endswagger-parameter %}

{% swagger-parameter in="query" required="true" name="social" type="String" %}
Indicator to include tickers that are trending as captured in the Social Dashboard.



Accepted Values:

`?social= 'reddit'`

`?social= 'stocktwits'`

`?social= 'twitter'`
{% endswagger-parameter %}

{% swagger-parameter in="query" required="true" name="isCrypto" type="String" %}
social media source you wish to return social insights for a given ticker.



**Accepted Values:**

`?isCrypto= 'true'`

`?isCrypto= 'false'`
{% endswagger-parameter %}

{% swagger-parameter in="query" name="timestamp" type="String" required="true" %}
The overall time horizon specified to capture social insights for.



**Accepted Values:**

`'24h'`

`'72h'`
{% endswagger-parameter %}

{% swagger-parameter in="query" name="bucket" type="String" required="true" %}
The bucket parameter defines the interval frequency of social insights within a measured time horizon.



**Accepted Values:**

**'15m'**

**'1hr'**
{% endswagger-parameter %}

{% swagger-parameter in="query" name="charts" type="String" required="true" %}
The charts parameter defines the type of social insight that can be returned in this query. You can specify one type of chart or multiple charts.



Accepted Values:

`posts`,

`comments`,

`likes`,

`impressions`

``

`E.g: ?`

`charts=impressions`

`charts=posts,comments,likes,impressions`


{% endswagger-parameter %}

{% swagger-parameter in="header" required="true" name="Content-Type" type="String" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" required="true" name="Authorization" type="String" %}
${YOUR_APIKEY}
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="" %}
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

