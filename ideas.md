---
description: >-
  The ideas API retrieves ideas from users on Utradea. Ideas can be searched by
  ticker, start, end date, & popularity.
---

# 💡 Ideas

All **GET methods** associated with retrieving Utradea's user-generated ideas/positions.

```
// GET IDEAS
https://cloud.utradea.com/v1/get-ideas
```

{% hint style="info" %}
You must **pass the required headers** with your enterprise access token.

Expand the below GET method table for details.
{% endhint %}

## Endpoints

{% swagger method="get" path="https://cloud.utradea.com/v1/get-ideas" baseUrl="URL: " summary="/get-ideas" %}
{% swagger-description %}
Request ideas by ticker, start and end date.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
${YOUR_APIKEY}
{% endswagger-parameter %}

{% swagger-parameter in="query" required="true" name="tickers" %}
The company OR crypto symbol, as it is defined in Utradea. To pass multiple symbols, use a comma to seperate tickers.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="startDate" type="Integer" %}
Integer representation of a date-time object. 
{% endswagger-parameter %}

{% swagger-parameter in="query" name="extend" type="String" %}
Pass '

**true**

' or '

**false**

' to return the condensed or  detailed version of the ideas object.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful requests will return the following response." %}
```javascript
{
    statusCode 200,
    "output": [
      {
        "premium": false,
        "catalysts": [
            "news",
            "secFiling",
            "otherCatalyst"
        ],
        "username": "joeytribbiani",
        "ticker": "TSLA",
        "entryPrice": 1184.69,
        "slug": "Random-idea_0",
        "positionStatus": "new-submission",
        "positionTitle": "Random idea",
        "targetPrice": 1303.16,
        "sentiment": "bullish",
        "confidence": 1,
        "durationIndex": "< 1 Week",
        "analysisType": "general",
        "contentText": "Testing Testing Testing\n\n\n\n\nTesting Testing Testing\n\n\n\n\nTesting Testing Testing\n\n\n\n\n\n\n\nTesting Testing Testing",
        "createdAt": "2021-11-08T19:19:10.805Z",
        "commentsCount": 0,
        "upvotedownvoteCount": 0,
        "upvotes": 0,
        "downvotes": 0
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

****

{% tabs %}
{% tab title="Node.js" %}
```javascript
const axios = require("axios")

const getIdeas = async () => new Promise((resolve, reject) => {
    var options = {
        method: 'GET',
        url: 'https://cloud.utradea.com/v1/get-ideas?ticker=PLTR,GOOGL,FB&?start=20211102?end=20211103',
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

{% tab title="Sample JSON Response" %}
```javascript
{
  "output": [
    {
      "premium": false,
      "catalysts": [
        "news",
        "secFiling",
        "otherCatalyst"
      ],
      "username": "joeytribbiani",
      "ticker": "TSLA",
      "entryPrice": 1184.69,
      "slug": "Random-idea_0",
      "positionStatus": "new-submission",
      "positionTitle": "Random idea",
      "targetPrice": 1303.16,
      "sentiment": "bullish",
      "confidence": 1,
      "durationIndex": "< 1 Week",
      "analysisType": "general",
      "contentText": "Testing Testing Testing\n\n\n\n\nTesting Testing Testing\n\n\n\n\nTesting Testing Testing\n\n\n\n\n\n\n\nTesting Testing Testing",
      "createdAt": "2021-11-08T19:19:10.805Z",
      "commentsCount": 0,
      "upvotedownvoteCount": 0,
      "upvotes": 0,
      "downvotes": 0
    },
    {
      "catalysts": [
        "sentiment",
        "secFiling"
      ],
      "username": "RajnishK",
      "ticker": "TSLA",
      "entryPrice": 706.92,
      "slug": "Image-rendering-for-position",
      "positionStatus": "new-submission",
      "positionTitle": "Image rendering for position",
      "targetPrice": 777.61,
      "sentiment": "bullish",
      "confidence": 1,
      "durationIndex": "< 1 Week",
      "analysisType": "general",
      "contentText": "test image rendering asd\n\nhttps://www.cleverfiles.com/howto/wp-content/uploads/2018/03/minion.jpg asdasddasdas asdas asda dasdsadasdasdasdasdasdasdasdasdasdasd asd asdsad asdkjaskljd lajdklasjdlkjaslkdalkjlkasjdlkasj dlkasjdlkasjdlkajsdlkajsld kajslkdjaslkd jlkasjdkla jdlkajsd",
      "createdAt": "2021-08-23T15:50:32.936Z",
      "commentsCount": 0,
      "upvotedownvoteCount": 0,
      "upvotes": 0,
      "downvotes": 0
    },
    {
      "catalysts": [
        "news",
        "secFiling"
      ],
      "username": "RajnishK",
      "ticker": "TSLA",
      "entryPrice": 704.175,
      "slug": "Test-image-render-position",
      "positionStatus": "new-submission",
      "positionTitle": "Test image render position",
      "targetPrice": 774.59,
      "sentiment": "bullish",
      "confidence": 1,
      "durationIndex": "< 1 Week",
      "analysisType": "general",
      "contentText": "rticipants. The WAX Blockchain uses Delegated Proof of Stake (DPoS) as its consensus mechanism and is fully backward compatible with EOS. asd https://www.cleverfiles.com/howto/wp-content/uploads/2018/03/minion.jpg testing image rendering",
      "createdAt": "2021-08-23T15:07:52.614Z",
      "commentsCount": 0,
      "upvotedownvoteCount": 0,
      "upvotes": 0,
      "downvotes": 0
    },
    {
      "catalysts": [
        "news",
        "secFiling"
      ],
      "username": "RajnishK",
      "ticker": "TSLA",
      "entryPrice": 704.175,
      "slug": "Test-position-for-image-render",
      "positionStatus": "new-submission",
      "positionTitle": "Test position for image render",
      "targetPrice": 774.59,
      "sentiment": "bullish",
      "confidence": 1,
      "durationIndex": "< 1 Week",
      "analysisType": "general",
      "contentText": "rticipants. The WAX Blockchain uses Delegated Proof of Stake (DPoS) as its consensus mechanism and is fully backward compatible with EOS.\n\n \n\nhere is image added in between post content",
      "createdAt": "2021-08-23T15:05:15.910Z",
      "commentsCount": 0,
      "upvotedownvoteCount": 0,
      "upvotes": 0,
      "downvotes": 0
    },
    {
      "catalysts": [
        "financials"
      ],
      "username": "kolhepalaash02",
      "ticker": "TSLA",
      "entryPrice": 689.075,
      "slug": "Aut-hscore-testing-payout-",
      "positionStatus": "closed-submission",
      "positionTitle": "Aut hscore testing payout",
      "targetPrice": 620.17,
      "sentiment": "bearish",
      "confidence": 5,
      "durationIndex": "< 1 Week",
      "analysisType": "fundamentals",
      "contentText": "Auth score testing payout ajsdlfkjsdakjfas",
      "createdAt": "2021-08-18T18:06:03.766Z",
      "exitPrice": 690.61,
      "exitedAt": "2021-08-18T18:38:49.212Z",
      "commentsCount": 0,
      "upvotedownvoteCount": 0,
      "upvotes": 0,
      "downvotes": 0
    },
    {
      "catalysts": [
        "secFiling",
        "news",
        "earningsRelease"
      ],
      "username": "Palaash2",
      "ticker": "TSLA",
      "entryPrice": 689.075,
      "slug": "auth-score-payout-testing",
      "positionStatus": "new-submission",
      "positionTitle": "auth score payout testing",
      "targetPrice": 757.98,
      "sentiment": "bullish",
      "confidence": 5,
      "durationIndex": "< 1 Week",
      "analysisType": "general",
      "contentText": "Testing for auth score payout",
      "createdAt": "2021-08-18T18:04:53.412Z",
      "commentsCount": 0,
      "upvotedownvoteCount": 0,
      "upvotes": 0,
      "downvotes": 0
    },
    {
      "catalysts": [
        "secFiling",
        "news",
        "earningsRelease"
      ],
      "username": "stockstothemoon",
      "ticker": "TSLA",
      "entryPrice": 646.22,
      "slug": "tsla-will-be-going-to-the-moon",
      "positionStatus": "new-submission",
      "positionTitle": "tsla will be going to the moon",
      "targetPrice": 710.84,
      "sentiment": "bullish",
      "confidence": 6,
      "durationIndex": "2-4 Weeks",
      "analysisType": "general",
      "contentText": "tsla is going to the moon",
      "createdAt": "2021-07-19T21:27:58.140Z",
      "commentsCount": 0,
      "upvotedownvoteCount": 0,
      "upvotes": 0,
      "downvotes": 0
    },
    {
      "catalysts": [
        "secFiling",
        "earningsRelease",
        "news"
      ],
      "username": "kolhepalaash02",
      "ticker": "TSLA",
      "entryPrice": 644.22,
      "slug": "Youtube-link-test",
      "positionStatus": "new-submission",
      "positionTitle": "Youtube link test",
      "targetPrice": 579.8,
      "sentiment": "bearish",
      "confidence": 5,
      "durationIndex": "2-4 Weeks",
      "analysisType": "general",
      "contentText": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque vel mattis massa. Aenean non urna vitae lectus gravida pulvinar id vitae erat. Curabitur ac iaculis nunc. Integer id mollis turpis, a condimentum justo. Mauris ligula risus, convallis sodales ligula nec, tristique dapibus turpis. Fusce consectetur arcu in tellus pharetra, ut volutpat arcu commodo. http://www.youtube.com/watch?v=-wtIMTCHWuI Praesent et mattis nunc. Ut sit amet ante nec tellus fermentum vehicula vitae ut erat.\n\nhttp://www.youtube.com/v/-wtIMTCHWuI?version=3&autohide=1\n\nhttp://youtu.be/-wtIMTCHWuI\n\nCras dignissim in eros quis interdum. Nunc non malesuada eros. Aenean maximus pharetra lacinia. Vestibulum pharetra urna et est bibendum, at porttitor magna pretium. Vivamus eu elit neque. Nunc eu est tristique, malesuada neque nec, pulvinar ex. Curabitur congue, quam eget tempor vulputate, nisi lectus mattis justo, a ornare sapien nibh et velit. Morbi eu porttitor ipsum.",
      "createdAt": "2021-07-18T23:23:10.921Z",
      "commentsCount": 0,
      "upvotedownvoteCount": 0,
      "upvotes": 0,
      "downvotes": 0
    },
    {
      "catalysts": [
        "secFiling",
        "earningsRelease",
        "news"
      ],
      "username": "kolhepalaash02",
      "ticker": "TSLA",
      "entryPrice": 649.3393,
      "slug": "Title",
      "positionStatus": "new-submission",
      "positionTitle": "Title",
      "targetPrice": 779.21,
      "sentiment": "bullish",
      "confidence": 5,
      "durationIndex": "2-4 Weeks",
      "analysisType": "general",
      "contentText": "AJSDKJD KJSDAKLFJDKLSJF KLSDJF LKDSAJ FLKDSJ A",
      "createdAt": "2021-07-08T19:39:54.534Z",
      "commentsCount": 0,
      "upvotedownvoteCount": 0,
      "upvotes": 0,
      "downvotes": 0
    },
    {
      "catalysts": [],
      "username": "jokinglol",
      "ticker": "TSLA",
      "entryPrice": 684.48,
      "slug": "TSLA-The-Bearish-Case",
      "positionStatus": "closed-submission",
      "positionTitle": "TSLA: The Bearish Case",
      "targetPrice": 683.51,
      "sentiment": "bearish",
      "confidence": 1,
      "durationIndex": "< 1 Week",
      "analysisType": "general",
      "contentText": "So, the Chinese state media has been shit talking Tesla for weeks, and their sales are plummeting in China as a result. After a woman protested Tesla at the Shanghai Auto Show in April, state media organs compared their cars to the Samsung Galaxy Note 7. Yes, really. Both in terms of production and sales, Tesla needs China. But does China need Tesla? With three viable EV startups on the market, the answer is no. First off, it is no coincidence that XPeng, Li Auto, and Nio all opened around 2015, when Tesla first started to become profitable. DiDi drove out Uber, Baidu drove out Google, and these theee EV startups will drive Tesla out of the biggest EV market in the world, because the Chinese government has a history of economic protectionism. They subsidize the fuck out of the industries they want developed, then force out Western companies by any means necessary. Look, I’m not saying “don’t invest in Tesla.” I’m saying consider the three EV startups in China, and watch that market very, very fucking closely. April, viral video of a woman protesting Tesla: https://www.cnbc.com/2021/04/23/tesla-in-china-pressure-mounts-on-carmaker-after-customer-protest.html April and May, sales go down as Chinese EV sales moon: https://www.cnbc.com/amp/2021/05/12/teslas-china-sales-tumble-in-april-from-march.html https://www.cnbc.com/amp/2021/06/09/teslas-china-sales-struggle-to-bounce-back-from-an-april-slump.html June, Tesla issues massive “soft recall” of over 200k Chinese vehicles amid regulator scrutiny (that is pretty much every Tesla vehicle in China): https://www.cnn.com/2021/06/28/business/tesla-china-recall-intl-hnk/index.html Note: In case this entire post does not make it abundantly clear, I have no positions in TSLA. I do, however, own XPeng and Li Auto stock.",
      "createdAt": "2021-06-30T19:05:08.635Z",
      "exitPrice": 679.89,
      "exitedAt": "2021-06-30T22:05:58.760Z",
      "commentsCount": 0,
      "upvotedownvoteCount": 0,
      "upvotes": 0,
      "downvotes": 0
    }
  ]
}
```



### Field Mappings

| Field Name     | Type     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| -------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| username       | String   | The username for a Utradea user.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ticker         | String   | The company or cryptocurrency symbol.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| positionTitle  | String   | Title of the idea posted.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| entryPrice     | Integer  | The price at the time the idea was posted.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| exitPrice      | Integer  | The price captured when the idea was closed on Utradea.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| targetPrice    | Float    | The price point that the user has set as the target price for their idea.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| positionStatus | String   | <p>The status of the position. </p><p>Accepted Values:</p><p><code>'new-submission'</code></p><p><code>'closed-submission'</code></p><p><code>'removed'</code></p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| slug           | String   | The url slug associated to an idea.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| analysisType   | String   | <p>The type of analysis performed with respect to the idea. </p><p></p><p><strong>Accepted Values:</strong></p><p><code>fundamental</code></p><p><code>general</code></p><p><code>technical</code></p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| catalysts      | Array    | <p>A catalyst is a flag that denotes what type of news or information supports a posted idea.</p><p></p><p><strong>Accepted Values:</strong></p><p><code>  news</code></p><p><code>  beta,</code></p><p><code>  bollingerBand,</code></p><p><code>  dividend,</code></p><p><code>  earningPerShare,</code></p><p><code>  earningsRelease,</code></p><p><code>  financials,</code></p><p><code>  management,</code></p><p><code>  movingAverage,</code></p><p><code>  news,</code></p><p><code>  otherCatalyst,</code></p><p><code>  'priceToEarningsRatio',</code></p><p><code>  'rsi',</code></p><p><code>  'secFiling',</code></p><p><code>  'sentiment',</code></p><p><code>  'volume'</code></p> |
| durationIndex  | Integer  | <p>The duration index measures the time-horizon of an idea.</p><p></p><p>Index Values:</p><p><code>&#x3C; 1 Week</code></p><p><code>1-2 Weeks</code></p><p><code>2-4 Weeks</code></p><p><code>1-2 Months</code></p><p><code>2-6 Months</code></p><p><code>6-12 Months</code></p><p><code>1-3 Years</code></p><p><code>3+ Years</code></p>                                                                                                                                                                                                                                                                                                                                                            |
| createdAt      | Datetime | The date was recorded at the time the idea was created.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| exitedAt       | Datetime | The date was recorded at the time the idea was closed (`positionStatus` == 'closed submission').                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| confidence     | Integer  | <p>The confidence index value represents how confident the user thinks their idea is relative to the target price they set.</p><p></p><p>Index Values:</p><p>1-10</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| contentText    | String   | The text commentary/analysis component of a posted idea.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| upvotes        | Integer  | The integer value represents the number of upvotes that an idea has received on Utradea.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| downvotes      | Integer  | The integer value represents the number of downvotes that an idea has received on Utradea.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| commentsCount  | Integer  | The integer value represents the number of comments that an idea has received on Utradea.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
{% endtab %}
{% endtabs %}
