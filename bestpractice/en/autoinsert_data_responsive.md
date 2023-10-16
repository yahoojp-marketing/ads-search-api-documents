# Ad Customizers feature (Responsive Search Ads Version)
## What is the “Ad Customizers”?
"Ad customizer" is a feature that will automatically feed designated data such as a text string or a fixed value into the title or description of the ad. <br>
It is also possible to use the countdown function to display a countdown of the time until the end of the sale.<br>
For more information about the Ad Customizer, please refer to the following help pages.<br>
・<a href="https://ads-help.yahoo-net.jp/s/article/H000044652?language=en_US">Ad customizer</a><br>
・<a href="https://ads-help.yahoo-net.jp/s/article/H000044220?language=en_US">What is Responsive Ads for Search</a><br>

## How to operate from Search Ads API
The Search Ads API uses the following Service to use the Ad Customizer.

##### 1. CustomizerAttributeService
You can get/add/remove customizer attributes by using this.<br>
When adding configuration information between account/campaign/ad group/keywords and customizer attributes, please add the customizer attributes first.<br>

##### 2. AccountCustomizerService
You can get/add/remove configuration information between account and customizer attributes by using this.

##### 3. CampaignCustomizerService
You can get/add/remove configuration information between campaign and customizer attributes by using this.

##### 4. AdGroupCustomizerService
You can get/add/remove configuration information between ad groups and customizer attributes by using this.

##### 5. AdGroupCriterionCustomizerService
You can get/add/remove configuration information between keywords and customizer attributes by using this.

##### 6. AdGroupAdService
You can get/add/remove information related to advertisements that insert registered data (ads with functions for data insertion) by using this.

## Scenerio Sample
As part of their promotional campaign, Company A is plannning to create the following dataset with the Search Ads API.

##### Sale product list
<table class="standard">
  <tr>
    <th valign="top">Account Name<br>（AccountId）</th>
    <th valign="top">Campaign Name<br>（CampaignId）</th>
    <th valign="top">Ad Group Name<br>（AdGroupId）</th>
    <th valign="top">Keyword<br>（CriterionId）</th>
    <th valign="top">Product<br>（TEXT）</th>
    <th valign="top">Lowest Price<br>（PRICE）</th>
    <th valign="top">Number of Models<br>（NUMBER）</th>
    <th valign="top">Discount Rate<br>（PERCENT）</th>
  </tr>
  <tr>
    <th valign="top">Test 150<br>（111111）</th>
    <th valign="top"></th>
    <th valign="top"></th>
    <th valign="top"></th>
    <th valign="top">Newest Models</th>
    <th valign="top">$100</th>
    <th valign="top">50</th>
    <th valign="top">10%</th>
  </tr>
  <tr>
    <th valign="top">Test 150<br>（111111）</th>
    <th valign="top">Electronics Sale<br>（222222）</th>
    <th valign="top"></th>
    <th valign="top"></th>
    <th valign="top">Affordable Electronics</th>
    <th valign="top">$80</th>
    <th valign="top">100</th>
    <th valign="top">10%</th>
  </tr>
  <tr>
    <th valign="top">Test 150<br>（111111）</th>
    <th valign="top">Electronics Sale<br>（222222）</th>
    <th valign="top">TVs<br>（333333）</th>
    <th valign="top"></th>
    <th valign="top">Popular TVs</th>
    <th valign="top">$500</th>
    <th valign="top">30</th>
    <th valign="top">20%</th>
  </tr>
  <tr>
    <th valign="top">Test 150<br>（111111）</th>
    <th valign="top">Electronics Sale<br>（222222）</th>
    <th valign="top">TVs<br>（333333）</th>
    <th valign="top">4K<br>（444444）</th>
    <th valign="top">4K TVs</th>
    <th valign="top">$800</th>
    <th valign="top">8</th>
    <th valign="top">30%</th>
  </tr>
</table>
*For each account, up to 40 attribute names can be registered.<br>
*In the case where different attribute values are registered with the same attribute name at the account/campaign/ad group/keyword level, the settings of the lower-level entity take priority during delivery.<br>

#### 1.	CustomizerAttributeService
Add customizer attributes with CustomizerAttributeService:add.<br>

##### Request Sample
```json
{
  "accountId": 111111,
  "operand": [
    {
      "name": "Product",
      "type": "TEXT"
    },
    {
      "name": "LowestPrice",
      "type": "PRICE"
    },
    {
      "name": "NumberOfModels",
      "type": "NUMBER"
    },
    {
      "name": "DiscountRate",
      "type": "PERCENT"
    }
  ]
}
```
##### Response Sample
```json
{
    "errors": null,
    "rid": "23eed375ce1c2d467d88ecaebc22b68c",
    "rval": {
        "values": [
            {
                "errors": null,
                "customizerAttribute": {
                    "accountId": 111111,
                    "customizerAttributeId": 555555,
                    "name": "Product",
                    "type": "TEXT"
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "customizerAttribute": {
                    "accountId": 111111,
                    "customizerAttributeId": 666666,
                    "name": "LowestPrice",
                    "type": "PRICE"
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "customizerAttribute": {
                    "accountId": 111111,
                    "customizerAttributeId": 777777,
                    "name": "NumberOfModels",
                    "type": "NUMBER"
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "customizerAttribute": {
                    "accountId": 111111,
                    "customizerAttributeId": 888888,
                    "name": "DiscountRate",
                    "type": "PERCENT"
                },
                "operationSucceeded": true
            }
        ]
    }
}
```
#### 2.	AccountCustomizerService
Add configuration information between an account and Customizer attributes with AccountCustomizerService:add.<br>

##### Request Sample
```json
{
  "accountId": 111111,
  "operand": [
    {
      "customizerAttributeId": 555555,
      "value": "Newest Models"
    },
    {
      "customizerAttributeId": 666666,
      "value": "$100"
    },
    {
      "customizerAttributeId": 777777,
      "value": "50"
    },
    {
      "customizerAttributeId": 888888,
      "value": "10%"
    }
  ]
}
```
##### Response Sample
```json
{
    "errors": null,
    "rid": "a10c6dd1f72911dc3a1cf2c3ac525790",
    "rval": {
        "values": [
            {
                "errors": null,
                "accountCustomizer": {
                    "accountId": 111111,
                    "customizerAttributeId": 555555,
                    "value": "Newest Models",
                    "approvalStatus": "REVIEW",
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "accountCustomizer": {
                    "accountId": 111111,
                    "customizerAttributeId": 666666,
                    "value": "$100",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "accountCustomizer": {
                    "accountId": 111111,
                    "customizerAttributeId": 777777,
                    "value": "50",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "accountCustomizer": {
                    "accountId": 111111,
                    "customizerAttributeId": 888888,
                    "value": "10%",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            }
        ]
    }
}

```
#### 3.	CampaignCustomizerService
Add configuration information between a campaign and Customizer attributes with CampaignCustomizerService:add.<br>

##### Request Sample
```json
{
  "accountId": 111111,
  "operand": [
    {
      "campaignId": 222222,
      "customizerAttributeId": 555555,
      "value": "Affordable Electronics"
    },
    {
      "campaignId": 222222,
      "customizerAttributeId": 666666,
      "value": "$80"
    },
    {
      "campaignId": 222222,
      "customizerAttributeId": 777777,
      "value": "100"
    },
    {
      "campaignId": 222222,
      "customizerAttributeId": 888888,
      "value": "10%"
    }
  ]
}
```
##### Response Sample
```json
{
    "errors": null,
    "rid": "ffde17246767f62feff67e26de6c8a79",
    "rval": {
        "values": [
            {
                "errors": null,
                "campaignCustomizer": {
                    "accountId": 111111,
                    "campaignId": 222222,
                    "customizerAttributeId": 555555,
                    "value": "Affordable Electronics",
                    "approvalStatus": "REVIEW",
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "campaignCustomizer": {
                    "accountId": 111111,
                    "campaignId": 222222,
                    "customizerAttributeId": 666666,
                    "value": "$80",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "campaignCustomizer": {
                    "accountId": 111111,
                    "campaignId": 222222,
                    "customizerAttributeId": 777777,
                    "value": "100",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "campaignCustomizer": {
                    "accountId": 111111,
                    "campaignId": 222222,
                    "customizerAttributeId": 888888,
                    "value": "10%",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            }
        ]
    }
}
```
#### 4.	AdGroupCustomizerService
Add configuration information between an ad group and Customizer attributes with AdGroupCustomizerService:add.<br>

##### Request Sample
```json
{
  "accountId": 111111,
  "operand": [
    {
      "adGroupId": 333333,
      "customizerAttributeId": 555555,
      "value": "Popular TVs"
    },
    {
      "adGroupId": 333333,
      "customizerAttributeId": 666666,
      "value": "$500"
    },
    {
      "adGroupId": 333333,
      "customizerAttributeId": 777777,
      "value": "30"
    },
    {
      "adGroupId": 333333,
      "customizerAttributeId": 888888,
      "value": "20%"
    }
  ]
}
```
##### Response Sample
```json
{
    "errors": null,
    "rid": "07651bf1409e00247ad811ffd1004bb3",
    "rval": {
        "values": [
            {
                "errors": null,
                "adGroupCustomizer": {
                    "accountId": 111111,
                    "adGroupId": 333333,
                    "customizerAttributeId": 555555,
                    "value": "Popular TVs",
                    "approvalStatus": "REVIEW",
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "adGroupCustomizer": {
                    "accountId": 111111,
                    "adGroupId": 333333,
                    "customizerAttributeId": 666666,
                    "value": "$500",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "adGroupCustomizer": {
                    "accountId": 111111,
                    "adGroupId": 333333,
                    "customizerAttributeId": 777777,
                    "value": "30",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "adGroupCustomizer": {
                    "accountId": 111111,
                    "adGroupId": 333333,
                    "customizerAttributeId": 888888,
                    "value": "20%",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            }
        ]
    }
}
```
#### 5.	AdGroupCriterionCustomizerService
Add configuration information between a keyword and Customizer attributes with AdGroupCriterionCustomizerService:add.<br>

##### Request Sample
```json
{
  "accountId": 111111,
  "operand": [
    {
      "criterionId": 444444,
      "customizerAttributeId": 555555,
      "value": "4K TVs"
    },
    {
      "criterionId": 444444,
      "customizerAttributeId": 666666,
      "value": "$800"
    },
    {
      "criterionId": 444444,
      "customizerAttributeId": 777777,
      "value": "8"
    },
    {
      "criterionId": 444444,
      "customizerAttributeId": 888888,
      "value": "30%"
    }
  ]
}
```
##### Response Sample
```json
{
    "errors": null,
    "rid": "080fded16a1a522fce1c4432dc3b13b7",
    "rval": {
        "values": [
            {
                "errors": null,
                "adGroupCustomizer": {
                    "accountId": 111111,
                    "criterionId": 444444,
                    "customizerAttributeId": 555555,
                    "value": "4K TVs",
                    "approvalStatus": "REVIEW",
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "adGroupCustomizer": {
                    "accountId": 111111,
                    "criterionId": 444444,
                    "customizerAttributeId": 666666,
                    "value": "$800",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "adGroupCustomizer": {
                    "accountId": 111111,
                    "criterionId": 444444,
                    "customizerAttributeId": 777777,
                    "value": "8",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "adGroupCustomizer": {
                    "accountId": 111111,
                    "criterionId": 444444,
                    "customizerAttributeId": 888888,
                    "value": "30%",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            }
        ]
    }
}
```
#### 6.	AdGroupAdService
Add an ad that inserts registered data (using a function for data insertion) with AdGroupAdService:add. <br>
By using the countdown function, you can display the remaining time until the end of a sale or campaign within the ad. The asset containing the countdown will become inactive once the countdown is finished.<br>
<br>
Therefore, assets with the countdown function should not be counted towards the minimum number of Headlines and Descriptions. However, they should still count towards the maximum number. For example, while a minimum of two Descriptions are required, and a maximum of four Descriptions are allowed, this includes both Descriptions with the countdown function (minimum two) and Descriptions without any countdown (maximum four).<br>
<br>
For more details on the countdown function for Responsive Search Ads, please refer to the following help documentation.<br>
・<a href="https://ads-help.yahoo-net.jp/s/article/H000044277?language=en_US">COUNTDOWN function (for Responsive Ads for Search)</a>

##### Request Sample
```json
{
  "accountId": 111111,
  "operand": [
    {
      "ad": {
        "adType": "RESPONSIVE_SEARCH_AD",
        "finalUrl": "http://www.example.jp",
        "responsiveSearchAd": {
          "headlines": [
            {
              "text": "{CUSTOMIZER.Product:Default Value} is a great deal",
              "pinnedField": "HEADLINE1"
            },
            {
              "text": "{CUSTOMIZER.LowestPrice:Default Value} at a reasonable price",
              "pinnedField": "HEADLINE2"
            },
            {
              "text": "Now {CUSTOMIZER.DisctountRate:Default Value} Off",
              "pinnedField": "HEADLINE3"
            },
            {
              "text": "Only {COUNTDOWN(2022-06-01 00:00:00,30)} left",
              "pinnedField": "UNSPECIFIED"
            }
          ],
          "descriptions": [
            {
              "text": "For a limited time only, get the latest model of {CUSTOMIZER.Product:Default Value} for just {CUSTOMIZER.LowestPrice:Default Value}!",
              "pinnedField": "DESCRIPTION1"
            },
            {
              "text": "All models of {CUSTOMIZER.NumberOfModels:Default Value} are {CUSTOMIZER.DiscountRate:Default Value} off or more",
              "pinnedField": "DESCRIPTION2"
            },
            {
              "text": "Only {COUNTDOWN(2022-06-01 00:00:00,30)} left, so don't miss out!",
              "pinnedField": "UNSPECIFIED"
            }
          ]
        }
      },
      "adGroupId": 333333,
      "adName": "Auto Ads",
      "campaignId": 222222,
      "userStatus": "ACTIVE"
    }
  ]
}
```
##### Response Sample
```json
{
    "errors": null,
    "rid": "50ec2df1d0bc693de9289fef50bd9045",
    "rval": {
        "values": [
            {
                "adGroupAd": {
                    "accountId": 111111,
                    "ad": {
                        "adType": "RESPONSIVE_SEARCH_AD",
                        "smartphoneFinalUrl": null,
                        "finalUrl": "http://www.example.jp",
                        "appAd": null,
                        "customParameters": null,
                        "description1": null,
                        "devicePreference": null,
                        "displayUrl": "www.example.jp",
                        "extendedTextAd": null,
                        "responsiveSearchAd": {
                            "headlines": [
                                {
                                  "text": "{CUSTOMIZER.Product:Default Value} is a great deal",
                                  "pinnedField": "HEADLINE1",
                                  "approvalStatus": "REVIEW",
                                  "disapprovalReasonCodes": null
                                },
                                {
                                  "text": "{CUSTOMIZER.LowestPrice:Default Value} at a reasonable price",
                                  "pinnedField": "HEADLINE2",
                                  "approvalStatus": "REVIEW",
                                  "disapprovalReasonCodes": null
                                },
                                {
                                  "text": "Now {CUSTOMIZER.DisctountRate:Default Value} Off",
                                  "pinnedField": "HEADLINE3",
                                  "approvalStatus": "REVIEW",
                                  "disapprovalReasonCodes": null
                                },
                                {
                                  "text": "Only {COUNTDOWN(2022-06-01 00:00:00,30)} left",
                                  "pinnedField": "UNSPECIFIED",
                                  "approvalStatus": "REVIEW",
                                  "disapprovalReasonCodes": null
                                }
                            ],
                            "descriptions": [
                                {
                                  "text": "For a limited time only, get the latest model of {CUSTOMIZER.Product:Default Value} for just {CUSTOMIZER.LowestPrice:Default Value}!",
                                  "pinnedField": "DESCRIPTION1",
                                  "approvalStatus": "REVIEW",
                                  "disapprovalReasonCodes": null
                                },
                                {
                                  "text": "All models of {CUSTOMIZER.NumberOfModels:Default Value} are {CUSTOMIZER.DiscountRate:Default Value} off or more",
                                  "pinnedField": "DESCRIPTION2",
                                  "approvalStatus": "REVIEW",
                                  "disapprovalReasonCodes": null
                                },
                                {
                                  "text": "Only {COUNTDOWN(2022-06-01 00:00:00,30)} left, so don't miss out!",
                                  "pinnedField": "UNSPECIFIED",
                                  "approvalStatus": "REVIEW",
                                  "disapprovalReasonCodes": null
                                }
                            ],
                            "path1": null,
                            "path2": null
                        },
                        "headline1": null,
                        "textAd2": null,
                        "dynamicSearchLinkedAd": null,
                        "trackingUrl": null,
                        "url": null
                    },
                    "adGroupId": 333333,
                    "adGroupName": "TVs",
                    "adGroupTrackId": 134525846777,
                    "adId": 999999,
                    "adName": "Auto Ads",
                    "adTrackId": 0,
                    "approvalStatus": "REVIEW",
                    "campaignId": 222222,
                    "campaignName": "Electronics Sale",
                    "campaignTrackId": 17246010137,
                    "disapprovalReasonCodes": null,
                    "feedId": null,
                    "invalidedTrademarks": null,
                    "labels": null,
                    "trademarkStatus": "NO_RESTRICTION",
                    "userStatus": "ACTIVE",
                    "createdDate": "20220513"
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
