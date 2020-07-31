# Ad Customizers feature (Data Assignment)
## What is “Ad Customizers”?
Ad Customizers is a function of changing the title and descriptions of the Search ads in dynamic.<br>
It can automatically insert the ad title and description flexibly. And 'COUNTDOWN' function will enable the feature to count down remaining minutes on discount sale.<br>

## How to operate from Search Ads API
To display ads by using Ad Customizers feature, use the three services below from Search Ads API.

##### 1.	FeedService 
FeedService can retrieve and add/update/delete the Feed information. <br>
Feed is a component to store Data Assignment List which added data to be inserted to ads.
  
##### 2.	FeedItemService  
FeedItemService can add/update/delete data to/from each Data Assignment List in Feed information.

##### 3.	AdGroupAdService
AdGroupAdService can create the ads which is inserted the data already added to the list (ads using a function to insert data).

## Examples
Company A is planning to add the data list below by Search Ads API for the promotion.
  
##### Sale product list
<table class="standard">
                <tr>
                    <th valign="top" >
                        <p>Product (String)</p>
                    </th>
                    <th valign="top" >
                        <p>Price (Price)</p>
                    </th>
                    <th valign="top">
                        <p>Final sale date (Date)</p>
                    </th>
                    <th valign="top" >
                        <p>CampaignId</p>
                    </th>
                    <th valign="top" >
                        <p>AdGroupId</p>
                    </th>
                </tr>
                <tr>
                    <td valign="top">
                        <p>Product 101</p>
                    </td>
                    <td valign="top">
                        <p>100</p>
                    </td>
                    <td valign="top">
                        <p>20151231 000000</p>
                    </td>
                    <td valign="top">
                        <p>500001</p>
                    </td>
                    <td valign="top">
                        <p>600001</p>
                    </td>
                </tr>
                <tr>
                    <td valign="top">
                        <p>Product 102</p>
                    </td>
                    <td valign="top">
                        <p>300</p>
                    </td>
                    <td valign="top">
                        <p>20151231 000000</p>
                    </td>
                    <td valign="top">
                        <p>500001</p>
                    </td>
                    <td valign="top">
                        <p>600001</p>
                    </td>
                </tr>
                <tr>
                    <td valign="top">
                        <p>Product 103</p>
                    </td>
                    <td valign="top">
                        <p>1,000</p>
                    </td>
                    <td valign="top">
                        <p>20151231 000000</p>
                    </td>
                    <td valign="top">
                        <p>500002</p>
                    </td>
                    <td valign="top">
                        <p>600002</p>
                    </td>
                </tr>
</table>
*Setting CampaignId and AdGroupId will enable to specify campaign and ad group to be used for the data line. <br>

#### 1.	Adding Feed
Add Feed to Search account using FeedService:add. <br>
For this example, "Sale product list" will be added to the account of company A (ID: 100000001).

##### Request Sample
```json
{
  "accountId": 111111,
  "operand": [
    {
      "feedAttribute": [
        {
          "feedAttributeName": "Product",
          "placeholderField": "AD_CUSTOMIZER_STRING"
        },
        {
          "feedAttributeName": "Price",
          "placeholderField": "AD_CUSTOMIZER_PRICE"
        },
        {
          "feedAttributeName": "Final sale date",
          "placeholderField": "AD_CUSTOMIZER_DATE"
        }
      ],
      "feedName": "Sale product list",
      "placeholderType": "AD_CUSTOMIZER"
    }
  ]
}
```

##### Response Sample
```json
{
    "errors": null,
    "rid": "ef342deaaff83579b7442f441a776e46",
    "rval": {
        "values": [
            {
                "errors": null,
                "feed": {
                    "accountId": 111111,
                    "domain": null,
                    "feedAttribute": [
                        {
                            "feedAttributeId": 1,
                            "feedAttributeName": "Product",
                            "placeholderField": "AD_CUSTOMIZER_STRING"
                        },
                        {
                            "feedAttributeId": 2,
                            "feedAttributeName": "Price",
                            "placeholderField": "AD_CUSTOMIZER_PRICE"
                        },
                        {
                            "feedAttributeId": 3,
                            "feedAttributeName": "Final sale date",
                            "placeholderField": "AD_CUSTOMIZER_DATE"
                        }
                    ],
                    "feedId": 222222,
                    "feedName": "Sale product list",
                    "feedTrackId": 0,
                    "placeholderType": "AD_CUSTOMIZER"
                },
                "operationSucceeded": true
            }
        ]
    }
}
```

#### 1.1.	Adding Campaign
Before add FeedItem, Add 2 Campaigns using CampaignService:add. <br>

##### Request Sample 1
```json
{
  "accountId": 111111,
  "operand": [
    {
      "biddingStrategyConfiguration": {
        "biddingScheme": {
          "biddingStrategyType": "MANUAL_CPC",
          "manualCpcBiddingScheme": {
            "enhancedCpcEnabled": "TRUE"
          }
        },
        "biddingStrategyType": "MANUAL_CPC"
      },
      "budget": {
        "amount": 100,
        "budgetPeriod": "DAILY"
      },
      "campaignName": "ad_campaign_1",
      "userStatus": "ACTIVE"
    }
  ]
}
```

##### Response Sample 1
```json
{
    "errors": null,
    "rid": "773e48f54e0395a7e38562b1e3cc4274",
    "rval": {
        "values": [
            {
                "campaign": {
                    "accountId": 111111,
                    ...
                    "campaignId": 500001,
                    "campaignName": "ad_campaign_1",
                    ...
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```

##### Request Sample 2
```json
{
  "accountId": 111111,
  "operand": [
    {
      "biddingStrategyConfiguration": {
        "biddingScheme": {
          "biddingStrategyType": "MANUAL_CPC",
          "manualCpcBiddingScheme": {
            "enhancedCpcEnabled": "TRUE"
          }
        },
        "biddingStrategyType": "MANUAL_CPC"
      },
      "budget": {
        "amount": 100,
        "budgetPeriod": "DAILY"
      },
      "campaignName": "ad_campaign_2",
      "userStatus": "ACTIVE"
    }
  ]
}
```

##### Response Sample 2
```json
{
    "errors": null,
    "rid": "7a322c9bef0ae56ec1d7e171f7dca6e7",
    "rval": {
        "values": [
            {
                "campaign": {
                    "accountId": 111111,
                    ...
                    "campaignId": 500002,
                    "campaignName": "ad_campaign_2",
                    ...
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```

#### 1.2.	Adding AdGroup
Before add FeedItem to , Add 2 Campaigns using CampaignService:add. <br>

##### Request Sample for autoinsert_data_adgroup
```json
{
  "accountId": 111111,
  "operand": [
    {
      "adGroupName": "ad_adgroup_1",
      "campaignId": 500001,
      "userStatus": "ACTIVE"
    }
  ]
}
```

##### Response Sample for autoinsert_data_adgroup
```json
{
    "errors": null,
    "rid": "aabdb67d885e287562b2688ff4fc6ec2",
    "rval": {
        "values": [
            {
                "adGroup": {
                    "accountId": 111111,
                    ...
                    "adGroupId": 600001,
                    "adGroupName": "ad_adgroup_1",
                    ...
                    "campaignId": 500001,
                    "campaignName": "ad_campaign_1",
                    ...
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```

##### Request Sample for autoinsert_data_adgroup2
```json
{
  "accountId": 111111,
  "operand": [
    {
      "adGroupName": "ad_adgroup_2",
      "campaignId": 500002,
      "userStatus": "ACTIVE"
    }
  ]
}
```

##### Response Sample for autoinsert_data_adgroup2
```json
{
    "errors": null,
    "rid": "be5101cd7b5e84afd077d6b3e8bbb826",
    "rval": {
        "values": [
            {
                "adGroup": {
                    "accountId": 111111,
                    ...
                    "adGroupId": 600002,
                    "adGroupName": "ad_adgroup_2",
                    ...
                    "campaignId": 500002,
                    "campaignName": "ad_campaign_2",
                    ...
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
#### 1.3. Add 2 of keyword
Add 2 of keyword using AdGroupCriterionService:add, before set Feeditem.

##### Request Sample
```json
{
  "accountId": 111111,
  "operand": [
    {
      "adGroupId": 600001,
      ...
      "campaignId": 500001,
      "criterion": {
        "criterionType": "KEYWORD",
        "keyword": {
          "keywordMatchType": "EXACT",
          "text": "ad_keyword_1"
        }
      },
      "use": "BIDDABLE"
    },
    {
      "adGroupId": 600002,
      ...
      "campaignId": 500002,
      "criterion": {
        "criterionType": "KEYWORD",
        "keyword": {
          "keywordMatchType": "EXACT",
          "text": "ad_keyword_2"
        }
      },
      "use": "BIDDABLE"
    }
  ]
}
```
##### Response Sample
```json
{
    "errors": null,
    "rid": "b7c4b362530fa6b3f5094231134cefe9",
    "rval": {
        "values": [
            {
                "adGroupCriterion": {
                    "accountId": 111111,
                    "adGroupId": 600001,
                    "adGroupName": "ad_adgroup_1",
                    ...
                    "campaignId": 500001,
                    "campaignName": "ad_campaign_1",
                    ...
                    "criterion": {
                        ...
                        "keyword": {
                            "keywordMatchType": "EXACT",
                            "text": "ad_keyword_1"
                        }
                    },
                    "labels": null,
                    ...
                },
                "errors": null,
                "operationSucceeded": true
            },
            {
                "adGroupCriterion": {
                    "accountId": 111111,
                    "adGroupId": 600002,
                    "adGroupName": "ad_adgroup_2",
                    ...
                    "campaignId": 500002,
                    "campaignName": "ad_campaign_2",
                    ...
                    "criterion": {
                        ...
                        "keyword": {
                            "keywordMatchType": "EXACT",
                            "text": "ad_keyword_2"
                        }
                    },
                    "labels": null,
                    ...
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
#### 2.	Adding FeedItem
Next, use FeedItemService to set data to be inserted or to be set to the Feed that was created earlier.

##### Request Sample
```json
{
  "accountId": 111111,
  "operand": [
    {
      "feedId": 222222,
      "feedItemAttribute": [
        {
          "feedAttributeId": 1,
          "placeholderField": "AD_CUSTOMIZER_STRING",
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "Product 101"
          }
        },
        {
          "feedAttributeId": 2,
          "placeholderField": "AD_CUSTOMIZER_PRICE",
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "100"
          }
        },
        {
          "feedAttributeId": 3,
          "placeholderField": "AD_CUSTOMIZER_DATE",
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "20151231 000000"
          }
        }
      ],
      "targetingAdGroup": {
        "targetingAdGroupId": 600001
      },
      "targetingCampaign": {
        "targetingCampaignId": 500001
      },
      "targetingKeyword": {
        "keywordMatchType": "EXACT",
        "text": "ad_keyword_1"
      }
    },
    {
      "feedId": 222222,
      "feedItemAttribute": [
        {
          "feedAttributeId": 1,
          "placeholderField": "AD_CUSTOMIZER_STRING",
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "Product 102"
          }
        },
        {
          "feedAttributeId": 2,
          "placeholderField": "AD_CUSTOMIZER_PRICE",
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "300"
          }
        },
        {
          "feedAttributeId": 3,
          "placeholderField": "AD_CUSTOMIZER_DATE",
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "20151231 000000"
          }
        }
      ],
      "targetingAdGroup": {
        "targetingAdGroupId": 600001
      },
      "targetingCampaign": {
        "targetingCampaignId": 500001
      },
      "targetingKeyword": {
        "keywordMatchType": "EXACT",
        "text": "ad_keyword_1"
      }
    },
    {
      "feedId": 222222,
      "feedItemAttribute": [
        {
          "feedAttributeId": 1,
          "placeholderField": "AD_CUSTOMIZER_STRING",
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "Product 103"
          }
        },
        {
          "feedAttributeId": 2,
          "placeholderField": "AD_CUSTOMIZER_PRICE",
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "1000"
          }
        },
        {
          "feedAttributeId": 3,
          "placeholderField": "AD_CUSTOMIZER_DATE",
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "20151231 000000"
          }
        }
      ],
      "targetingAdGroup": {
        "targetingAdGroupId": 600002
      },
      "targetingCampaign": {
        "targetingCampaignId": 500002
      },
      "targetingKeyword": {
        "keywordMatchType": "EXACT",
        "text": "ad_keyword_2"
      }
    }
  ],
  "placeholderType": "AD_CUSTOMIZER"
}
```

##### Response Sample
```json
{
    "errors": null,
    "rid": "a43f4e255655225bbc4c1b579a72ac34",
    "rval": {
        "values": [
            {
                "errors": null,
                "feedItem": {
                    "accountId": 111111,
                    ...
                    "feedId": 222222,
                    "feedItemAttribute": [
                        {
                            "feedAttributeId": 1,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "AD_CUSTOMIZER_STRING",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "Product 101"
                            }
                        },
                        {
                            "feedAttributeId": 2,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "AD_CUSTOMIZER_PRICE",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "100"
                            }
                        },
                        {
                            "feedAttributeId": 3,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "AD_CUSTOMIZER_DATE",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "20151231 000000"
                            }
                        }
                    ],
                    "feedItemId": 300001,
                    ...
                    "placeholderType": "AD_CUSTOMIZER",
                    ...
                    "targetingAdGroup": {
                        "targetingAdGroupId": 600001
                    },
                    "targetingCampaign": {
                        "targetingCampaignId": 500001
                    },
                    "targetingKeyword": {
                        ...
                        "text": "ad_keyword_1"
                    },
                    "trademarkStatus": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "feedItem": {
                    "accountId": 111111,
                    ...
                    "feedId": 222222,
                    "feedItemAttribute": [
                        {
                            "feedAttributeId": 1,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "AD_CUSTOMIZER_STRING",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "Product 102"
                            }
                        },
                        {
                            "feedAttributeId": 2,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "AD_CUSTOMIZER_PRICE",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "300"
                            }
                        },
                        {
                            "feedAttributeId": 3,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "AD_CUSTOMIZER_DATE",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "20151231 000000"
                            }
                        }
                    ],
                    "feedItemId": 300002,
                    ...
                    "placeholderType": "AD_CUSTOMIZER",
                    ...
                    "targetingAdGroup": {
                        "targetingAdGroupId": 600001
                    },
                    "targetingCampaign": {
                        "targetingCampaignId": 500001
                    },
                    "targetingKeyword": {
                        ...,
                        "text": "ad_keyword_1"
                    },
                    "trademarkStatus": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "feedItem": {
                    "accountId": 111111,
                    ...
                    "feedId": 222222,
                    "feedItemAttribute": [
                        {
                            "feedAttributeId": 1,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "AD_CUSTOMIZER_STRING",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "Product 103"
                            }
                        },
                        {
                            "feedAttributeId": 2,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "AD_CUSTOMIZER_PRICE",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "1000"
                            }
                        },
                        {
                            "feedAttributeId": 3,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "AD_CUSTOMIZER_DATE",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "20151231 000000"
                            }
                        }
                    ],
                    "feedItemId": 300003,
                    ...
                    "placeholderType": "AD_CUSTOMIZER",
                    ...
                    "targetingAdGroup": {
                        "targetingAdGroupId": 600002
                    },
                    "targetingCampaign": {
                        "targetingCampaignId": 500002
                    },
                    "targetingKeyword": {
                        ...
                        "text": "ad_keyword_2"
                    },
                    "trademarkStatus": null
                },
                "operationSucceeded": true
            }
        ]
    }
}
```

#### 3.	Adding AdGroupAd
Then, use AdGroupAdService to create ads to be inserted added data to.<br>
In this example, two of different ads are created since Ad Customizer requires to enable ordinary ads and ads to be inserted data automatically.<br>
[Tips]<br>
Using 'COUNTDOWN' feature will enable to display remaining minutes of discount sales and campaign within the ad. And ad delivery can be paused at the same time as the end of countdown. <br>

##### Request Sample
```json
{
  "accountId": 111111,
  "operand": [
    {
      "ad": {
        "adType": "EXTENDED_TEXT_AD",
        "advancedUrl": "http://www.example.jp",
        "description": "Sold for {=Sale product list.Price} yen.",
        "extendedTextAd": {
          "headline2": "{=COUNTDOWN(Sale product list.Final sale date,\"en\")} to the end"
        },
        "headline": "great deal on a popular {=Sale product list.Product}."
      },
      "adGroupId": 600001,
      "adName": "Best Practice Auto Ads",
      "campaignId": 500001,
      "userStatus": "ACTIVE"
    },
    {
      "ad": {
        "adType": "EXTENDED_TEXT_AD",
        "advancedUrl": "http://www.example.jp",
        "description": "Sold at a special price for a limited time.",
        "extendedTextAd": {
          "headline2": "Until December 31st"
        },
        "headline": "great deal on a popular product"
      },
      "adGroupId": 600002,
      "adName": "Best Practice Simple Ads",
      "campaignId": 500002,
      "userStatus": "ACTIVE"
    }
  ]
}
```

##### Response Sample
```json
{
    "errors": null,
    "rid": "290c4614f7af6a46f619e2a08f7083a7",
    "rval": {
        "values": [
            {
                "adGroupAd": {
                    "accountId": 111111,
                    "ad": {
                        "adType": "EXTENDED_TEXT_AD",
                        ...
                        "advancedUrl": "http://www.example.jp",
                        ...
                        "description": "Sold for {=Sale product list.Price} yen.",
                        "devicePreference": null,
                        "displayUrl": "www.example.jp",
                        "extendedTextAd": {
                            "headline2": "{=COUNTDOWN(Sale product list.Final sale date,\"en\")} to the end",                  
                            ...
                        },                        
                        "headline": "great deal on a popular {=Sale product list.Product}.",
                        ...
                    },
                    "adGroupId": 600001,
                    "adGroupName": "ad_adgroup_1",
                    ...
                    "adName": "Best Practice Auto Ads",
                    ...
                    "campaignId": 500001,
                    "campaignName": "ad_campaign_1",
                    ...
                    "feedId": 222222,
                    ...
                },
                "errors": null,
                "operationSucceeded": true
            },
            {
                "adGroupAd": {
                    "accountId": 111111,
                    "ad": {
                        "adType": "EXTENDED_TEXT_AD",
                        ...
                        "advancedUrl": "http://www.example.jp",
                        ...
                        "description": "Sold at a special price for a limited time.",
                        "devicePreference": null,
                        "displayUrl": "www.example.jp",
                        "extendedTextAd": {
                            "headline2": "Until December 31st",
                            ...
                        },
                        "headline": "great deal on a popular product",
                        ...
                    },
                    "adGroupId": 600002,
                    "adGroupName": "ad_adgroup_2",
                    ...,
                    "adName": "Best Practice Simple Ads",
                    ...
                    "campaignId": 500002,
                    "campaignName": "ad_campaign_2",
                    ...
                    "feedId": null,
                    ...
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}

```

#### 4.	Change of FeedItem
Since some price changes occurred after creating ads, following data revision is required.<br>
Ad Customizers can change ad creatives automatically only with data updates, using FeedItemService.

##### Sale product list (After the change)
<table class="standard">
                <tr>
                    <th valign="top" >
                        <p>Product (String)</p>
                    </th>
                    <th valign="top" >
                        <p>Price (Price)</p>
                    </th>
                    <th valign="top">
                        <p>Final sale date (Date)</p>
                    </th>
                    <th valign="top" >
                        <p>CampaignId</p>
                    </th>
                    <th valign="top" >
                        <p>AdGroupId</p>
                    </th>
                </tr>
                <tr>
                    <td valign="top">
                        <p>Product 101</p>
                    </td>
                    <td valign="top">
                        <p>90</p>
                    </td>
                    <td valign="top">
                        <p>20151231 000000</p>
                    </td>
                    <td valign="top">
                        <p>500001</p>
                    </td>
                    <td valign="top">
                        <p>600001</p>
                    </td>
                </tr>
                <tr>
                    <td valign="top">
                        <p>Product 102</p>
                    </td>
                    <td valign="top">
                        <p>350</p>
                    </td>
                    <td valign="top">
                        <p>20151231 000000</p>
                    </td>
                    <td valign="top">
                        <p>500001</p>
                    </td>
                    <td valign="top">
                        <p>600001</p>
                    </td>
                </tr>
                <tr>
                    <td valign="top">
                        <p>Product 103</p>
                    </td>
                    <td valign="top">
                        <p>1,000</p>
                    </td>
                    <td valign="top">
                        <p>20151231 000000</p>
                    </td>
                    <td valign="top">
                        <p>500002</p>
                    </td>
                    <td valign="top">
                        <p>600002</p>
                    </td>
                </tr>
</table>

##### Request Sample
```json
{
  "accountId": 111111,
  "operand": [
    {
      "feedItemAttribute": [
        {
          "feedAttributeId": 2,
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "90"
          }
        }
      ],
      "feedItemId": 300001,
      "targetingAdGroup": {
        "targetingAdGroupId": 600001
      },
      "targetingCampaign": {
        "targetingCampaignId": 500001
      }
    },
    {
      "feedItemAttribute": [
        {
          "feedAttributeId": 2,
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "350"
          }
        }
      ],
      "feedItemId": 300002,
      "targetingAdGroup": {
        "targetingAdGroupId": 600001
      },
      "targetingCampaign": {
        "targetingCampaignId": 500001
      }
    },
    {
      "feedItemId": 300003,
      "targetingAdGroup": {
        "targetingAdGroupId": 600002
      },
      "targetingCampaign": {
        "targetingCampaignId": 500002
      }
    }
  ],
  "placeholderType": "AD_CUSTOMIZER"
}
```

##### Response Sample
```json
{
    "errors": null,
    "rid": "d580edb35d2889a6184d7573ed51c339",
    "rval": {
        "values": [
            {
                "errors": null,
                "feedItem": {
                    "accountId": 111111,
                    ...
                    "feedId": 222222,
                    "feedItemAttribute": [
                        {
                            "feedAttributeId": 1,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "AD_CUSTOMIZER_STRING",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "Product 101"
                            }
                        },
                        {
                            "feedAttributeId": 2,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "AD_CUSTOMIZER_PRICE",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "90"
                            }
                        },
                        {
                            "feedAttributeId": 3,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "AD_CUSTOMIZER_DATE",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "20151231 000000"
                            }
                        }
                    ],
                    "feedItemId": 300001,
                    ...
                    "placeholderType": "AD_CUSTOMIZER",
                    ...
                    "targetingAdGroup": {
                        "targetingAdGroupId": 600001
                    },
                    "targetingCampaign": {
                        "targetingCampaignId": 500001
                    },
                    "targetingKeyword": {
                        ...
                        "text": "ad_keyword_1"
                    },
                    "trademarkStatus": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "feedItem": {
                    "accountId": 111111,
                    ...
                    "feedId": 222222,
                    "feedItemAttribute": [
                        {
                            "feedAttributeId": 1,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "AD_CUSTOMIZER_STRING",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": "Product 102",
                                "reviewFeedAttributeValue": null
                            }
                        },
                        {
                            "feedAttributeId": 2,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "AD_CUSTOMIZER_PRICE",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": "350",
                                "reviewFeedAttributeValue": null
                            }
                        },
                        {
                            "feedAttributeId": 3,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "AD_CUSTOMIZER_DATE",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": "20151231 000000",
                                "reviewFeedAttributeValue": null
                            }
                        }
                    ],
                    "feedItemId": 300002,
                    ...
                    "placeholderType": "AD_CUSTOMIZER",
                    ...
                    "targetingAdGroup": {
                        "targetingAdGroupId": 600001
                    },
                    "targetingCampaign": {
                        "targetingCampaignId": 500001
                    },
                    "targetingKeyword": {
                        ...
                        "text": "ad_keyword_1"
                    },
                    "trademarkStatus": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "feedItem": {
                    "accountId": 111111,
                    ...
                    "feedId": 222222,
                    "feedItemAttribute": [
                        {
                            "feedAttributeId": 1,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "AD_CUSTOMIZER_STRING",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": "Product 103",
                                "reviewFeedAttributeValue": null
                            }
                        },
                        {
                            "feedAttributeId": 2,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "AD_CUSTOMIZER_PRICE",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": "1000",
                                "reviewFeedAttributeValue": null
                            }
                        },
                        {
                            "feedAttributeId": 3,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "AD_CUSTOMIZER_DATE",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": "20151231 000000",
                                "reviewFeedAttributeValue": null
                            }
                        }
                    ],
                    "feedItemId": 300003,
                    ...
                    "placeholderType": "AD_CUSTOMIZER",
                    ...
                    "targetingAdGroup": {
                        "targetingAdGroupId": 600002
                    },
                    "targetingCampaign": {
                        "targetingCampaignId": 500002
                    },
                    "targetingKeyword": {
                        ...
                        "text": "ad_keyword_2"
                    },
                    "trademarkStatus": null
                },
                "operationSucceeded": true
            }
        ]
    }
}
```
