# Conversion Tracking
## What is "Conversion"?
Conversion is the number of users who clicked on an Ads and performed some "result" action.<br>
By measuring this, you can see how well your Ads is performing.<br>
For details, refer to the help below.<br>
・<a href="https://ads-help.yahoo-net.jp/s/article/H000045014?language=en_US">Conversion Analytics</a>

## How to operate from Search Ads API
Search Ads API uses ConversionTrackerService, to get, add and update conversion tracker information.<br>
By using this service, you can get the number of conversions from the advertisements displayed in search advertisements, and you can check how well the advertisements are performing.<br>
The conversion tag is shared with the ad management tool and API.

## Sample Scenario
Company A sells Product B for 10,000 yen. Create a conversion tracker to track conversions on your web page.

<table class="standard">
  <tr>
　　<th>Item</th>
　　<th>Value</th>
　　<th>Explain</th>
　</tr>
　<tr>
　　<td>category</td>
　　<td>PURCHASE</td>
　　<td>Conversion tracker info categories</td>
　</tr>
　<tr>
　　<td>conversionTrackerName</td>
　　<td>（Name it easy to understand）</td>
　　<td>Name of Conversion Tracker</td>
　</tr>
　<tr>
　　<td>conversionTrackerType</td>
　　<td>WEB_CONVERSION</td>
　　<td>Type of Conversion</td>
　</tr>
　<tr>
　　<td>measurementPeriod</td>
　　<td>30</td>
　　<td>Conversion measurement period（● days）</td>
　</tr>
　<tr>
　　<td>status</td>
　　<td>ENABLED</td>
　　<td>Status of Conversion Tracker Information</td>
　</tr>
　<tr>
　　<td>userRevenueValue</td>
　　<td>10000</td>
　　<td>Sales of one conversion when the sales amount is fixed（● yen）※Value of Product B</td>
　</tr>
　<tr>
　　<td>markupLanguage（webConversion）</td>
　　<td>HTML</td>
　　<td>Markup language used to write snippets</td>
　</tr>
　<tr>
　　<td>trackingCodeType（webConversion）</td>
　　<td>WEBPAGE</td>
　　<td>Web page tracking type</td>
　</tr>
</table>
<br>

#### 1.	Add Conversion Tracker Information
At first, add Conversion Tracker Information with ConversionTrackerService:add.

##### Request sample
```json
{
  "accountId": 111111,
  "operand": [
    {
      "category": "PURCHASE",
      "conversionTrackerName": "Pro_B_CV",
      "conversionTrackerType": "WEB_CONVERSION",
      "measurementPeriod": 30,
      "status": "ENABLED",
      "userRevenueValue": "10000",
      "webConversion": {
        "markupLanguage": "HTML",
        "trackingCodeType": "WEBPAGE"
      }
    }
  ]
}
```

##### Response sample
※Check for Response of snippet and advancedSnippet with ConversionTrackerService:get.
```json
{
    "errors": null,
    "rid": "f7eaf398417b6eea34b1274ce683469d",
    "rval": {
        "values": [
            {
                "conversionTracker": {
                    "accountId": 111111,
                    "allConversionValue": null,
                    "allConversions": null,
                    "appConversion": null,
                    "category": "PURCHASE",
                    "conversionCountingType": "MANY_PER_CLICK",
                    "conversionTrackerId": 222222,
                    "conversionTrackerName": "Pro_B_CV",
                    "conversionTrackerType": "WEB_CONVERSION",
                    "conversionValue": null,
                    "conversions": null,
                    "excludeFromBidding": "FALSE",
                    "measurementPeriod": 30,
                    "mostRecentConversionDate": null,
                    "status": "ENABLED",
                    "userRevenueValue": "10000",
                    "webConversion": {
                        "markupLanguage": "HTML",
                        "snippet": null,
                        "advancedSnippet": null,
                        "trackingCodeType": "WEBPAGE"
                    }
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
<br>

#### 2. Get comversion tags to measure
Get comversion tags to measure with ConversionTrackerService:get.<br>
※Check Conversion measurement tag (snippet or advancedSnippet) here.<br>
※Then you use advancedSnippet, you need site general tag. For details, refer to the help below.<br>
・<a href="https://ads-help.yahoo-net.jp/s/article/H000044574?language=en_US">Conversion Analytics</a>

##### Request sample
```json
{
  "accountId": 111111,
  "conversionTrackerIds": [
    222222
  ],
  "numberResults": 1,
  "startIndex": 1,
  "statuses": [
    "ENABLED"
  ],
  "trackingCodeTypes": [
    "WEBPAGE"
  ]
}
```

##### Response sample
```json
{
    "errors": null,
    "rid": "180b348e3630b1feef3a9ef24546e488",
    "rval": {
        "totalAllConversionValue": "0",
        "totalAllConversions": 0,
        "totalConversionValue": "0",
        "totalConversions": 0,
        "totalNumEntries": 1,
        "values": [
            {
                "conversionTracker": {
                    "accountId": 111111,
                    "allConversionValue": null,
                    "allConversions": null,
                    "appConversion": null,
                    "category": "PURCHASE",
                    "conversionCountingType": "MANY_PER_CLICK",
                    "conversionTrackerId": 222222,
                    "conversionTrackerName": "Pro_B_CV",
                    "conversionTrackerType": "WEB_CONVERSION",
                    "conversionValue": null,
                    "conversions": null,
                    "excludeFromBidding": "FALSE",
                    "measurementPeriod": 30,
                    "mostRecentConversionDate": null,
                    "status": "ENABLED",
                    "userRevenueValue": "10000",
                    "webConversion": {
                        "markupLanguage": "HTML",
                        "snippet": "<!-- Yahoo Code for your Conversion Page -->\n<script type=\"text/javascript\">\n    /* <![CDATA[ */\n    var yahoo_conversion_id = 1000000407;\n    var yahoo_conversion_label = \"S7vjCPKvk9oBEJ7fgOQD\";\n    var yahoo_conversion_value = 10000;\n    /* ]]> */\n</script>\n<script type=\"text/javascript\" src=\"https://s.yimg.jp/images/listing/tool/cv/conversion.js\">\n</script>\n<noscript>\n    <div style=\"display:inline;\">\n        <img height=\"1\" width=\"1\" style=\"border-style:none;\" alt=\"\" src=\"https://b91.yahoo.co.jp/pagead/conversion/1000000407/?value=10000&label=S7vjCPKvk9oBEJ7fgOQD&guid=ON&script=0&disvt=true\"/>\n    </div>\n</noscript>",
                        "advancedSnippet": "<script async>\nytag({\n  \"type\": \"yss_conversion\",\n  \"config\": {\n    \"yahoo_conversion_id\": \"1000000407\",\n    \"yahoo_conversion_label\": \"S7vjCPKvk9oBEJ7fgOQD\",\n    \"yahoo_conversion_value\": \"10000\"\n  }\n});\n</script>",
                        "trackingCodeType": "WEBPAGE"
                    }
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
<br>

#### 3. Add tags into website and start to measure conversion
Add tags of snippet or advancedSnippet into website.

#### 4. Get conversion measured
Get conversion measured with ConversionTrackerService:get.

##### Request sample
```json
{
  "accountId": 111111,
  "conversionTrackerIds": [
    222222
  ],
  "numberResults": 1,
  "startIndex": 1,
  "statuses": [
    "ENABLED"
  ],
  "trackingCodeTypes": [
    "WEBPAGE"
  ]
}
```

##### Response sample
```json
{
    "errors": null,
    "rid": "180b348e3630b1feef3a9ef24546e488",
    "rval": {
        "totalAllConversionValue": "10000000",
        "totalAllConversions": 1000,
        "totalConversionValue": "100000000",
        "totalConversions": 10000,
        "totalNumEntries": 1,
        "values": [
            {
                "conversionTracker": {
                    "accountId": 111111,
                    "allConversionValue": 10000000,
                    "allConversions": 1000,
                    "appConversion": null,
                    "category": "PURCHASE",
                    "conversionCountingType": "MANY_PER_CLICK",
                    "conversionTrackerId": 222222,
                    "conversionTrackerName": "Pro_B_CV",
                    "conversionTrackerType": "WEB_CONVERSION",
                    "conversionValue": 100000000,
                    "conversions": 10000,
                    "excludeFromBidding": "FALSE",
                    "measurementPeriod": 30,
                    "mostRecentConversionDate": null,
                    "status": "ENABLED",
                    "userRevenueValue": "10000",
                    "webConversion": {
                        "markupLanguage": "HTML",
                        "snippet": "<!-- Yahoo Code for your Conversion Page -->\n<script type=\"text/javascript\">\n    /* <![CDATA[ */\n    var yahoo_conversion_id = 1000000407;\n    var yahoo_conversion_label = \"S7vjCPKvk9oBEJ7fgOQD\";\n    var yahoo_conversion_value = 10000;\n    /* ]]> */\n</script>\n<script type=\"text/javascript\" src=\"https://s.yimg.jp/images/listing/tool/cv/conversion.js\">\n</script>\n<noscript>\n    <div style=\"display:inline;\">\n        <img height=\"1\" width=\"1\" style=\"border-style:none;\" alt=\"\" src=\"https://b91.yahoo.co.jp/pagead/conversion/1000000407/?value=10000&label=S7vjCPKvk9oBEJ7fgOQD&guid=ON&script=0&disvt=true\"/>\n    </div>\n</noscript>",
                        "advancedSnippet": "<script async>\nytag({\n  \"type\": \"yss_conversion\",\n  \"config\": {\n    \"yahoo_conversion_id\": \"1000000407\",\n    \"yahoo_conversion_label\": \"S7vjCPKvk9oBEJ7fgOQD\",\n    \"yahoo_conversion_value\": \"10000\"\n  }\n});\n</script>",
                        "trackingCodeType": "WEBPAGE"
                    }
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
<br>

#### 5.	Set Conversion Tracker Information
Set Conversion Tracker Information which were added with ConversionTrackerService:set.<br>
In the following, Set category of Conversion Tracker Information from PURCHASE to PAGE_VIEW.

##### Request sample
```json
{
  "accountId": 111111,
  "operand": [
    {
      "category": "PAGE_VIEW",
      "conversionTrackerId": 222222,
      "conversionTrackerType": "WEB_CONVERSION"
    }
  ]
}
```

##### Response sample
```json
{
    "errors": null,
    "rid": "5b5d34b5cd8238352127e418b2b4bacb",
    "rval": {
        "values": [
            {
                "conversionTracker": {
                    "accountId": 111111,
                    "allConversionValue": 10000000,
                    "allConversions": 1000,
                    "appConversion": null,
                    "category": "PAGE_VIEW",
                    "conversionCountingType": "MANY_PER_CLICK",
                    "conversionTrackerId": 222222,
                    "conversionTrackerName": "Pro_B_CV",
                    "conversionTrackerType": "WEB_CONVERSION",
                    "conversionValue": 100000000,
                    "conversions": 10000,
                    "excludeFromBidding": "FALSE",
                    "measurementPeriod": 30,
                    "mostRecentConversionDate": null,
                    "status": "ENABLED",
                    "userRevenueValue": "10000",
                    "webConversion": {
                        "markupLanguage": "HTML",
                        "snippet": "<!-- Yahoo Code for your Conversion Page -->\n<script type=\"text/javascript\">\n    /* <![CDATA[ */\n    var yahoo_conversion_id = 1000000407;\n    var yahoo_conversion_label = \"S7vjCPKvk9oBEJ7fgOQD\";\n    var yahoo_conversion_value = 10000;\n    /* ]]> */\n</script>\n<script type=\"text/javascript\" src=\"https://s.yimg.jp/images/listing/tool/cv/conversion.js\">\n</script>\n<noscript>\n    <div style=\"display:inline;\">\n        <img height=\"1\" width=\"1\" style=\"border-style:none;\" alt=\"\" src=\"https://b91.yahoo.co.jp/pagead/conversion/1000000407/?value=10000&label=S7vjCPKvk9oBEJ7fgOQD&guid=ON&script=0&disvt=true\"/>\n    </div>\n</noscript>",
                        "advancedSnippet": "<script async>\nytag({\n  \"type\": \"yss_conversion\",\n  \"config\": {\n    \"yahoo_conversion_id\": \"1000000407\",\n    \"yahoo_conversion_label\": \"S7vjCPKvk9oBEJ7fgOQD\",\n    \"yahoo_conversion_value\": \"10000\"\n  }\n});\n</script>",
                        "trackingCodeType": "WEBPAGE"
                    }
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
