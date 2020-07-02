# Ad Display Option
## What is “Ad Display Option”?
<A href="https://ads-help.yahoo.co.jp/yahooads/ss/articledetail?lan=en&aid=85&o=default">Ad Display Option</a> is a function of displaying additional information such as a link to other URL page or phone number to Search Ads.   
    
There are 4 features for Ad Display Option:  
* "QuickLink" (Displays a link to other URL page on bottom of the ads)
* "CallExtension" (Displays phone number).  
* “CALLOUT” (Options for supplementing text)
* “STRUCTURED_SNIPPET” (Options for supplementing category)
  
There are 2 advantages from using Ad Display Option.    
1. Ad spaces become larger and increase the visibility. This will raise the click rate.
2. Can easily access to the page user desires. This will raise the convenience.

## How to operate from Search Ads API
To display ads for Ad Display Option, use the three services below from Search Ads API.  
##### 1. FeedItemService 
FeedItemService can retrieve and add/update/delete the FeedItem.  
FeedItem is a component of text, URL link, or phone number to display as Ad Display Option.
  
##### 2. CampaignFeedService  
CampaignFeedService can set the FeedItem to campaign and retrieve the FeedItem that is set to campaign.
  
##### 3. AdGroupFeedService
AdGroupFeedService can set the FeedItem to ad group and retrieve the FeedItem that is set to ad group.  
  
## Examples
Company A is planning add the below Ad Display Option by Search Ads API for the promotion.
  
##### QuickLink
No                | LINK_TEXT             | LINK_URL                                 
----------------- | --------------------- | -----------------------------------------
1 | Sale | www.example.jp/sale
2 | Store List | www.example.jp/store
3 | Ranking | www.example.jp/ranking
4 | Support | www.example.jp/support
5 | Coupon | www.example.jp/coupon
6 | Special Sale | www.example.jp/specialsale
7 | Point Information | www.example.jp/point
   
##### CallExtension
No                | CALL_PHONE_NUMBER                                 
----------------- | ---------------------
1 | 0120-45-6789

#### 1.	Adding FeedItem
Add FeedItem to Search Ads account using FeedItemService.   
For this example, each Ad Display Option will be added to the account of company A (ID: 100000001).  
##### <Request Sample> [For QUICKLINK]
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "feedItemAttribute": [
      	{
      	  "placeholderField": "LINK_TEXT",	
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "Sale"
          }
      	},
      	{
      	  "placeholderField": "ADVANCED_URL",	
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "http://www.example.jp/sale"
          }
      	}
      ],
      "placeholderType": "QUICKLINK"
    },
    {
      "feedItemAttribute": [
      	{
      	  "placeholderField": "LINK_TEXT",	
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "Store List"
          }
      	},
      	{
      	  "placeholderField": "ADVANCED_URL",	
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "http://www.example.jp/store"
          }
      	}
      ],
      "placeholderType": "QUICKLINK"
    },
    {
      "feedItemAttribute": [
      	{
      	  "placeholderField": "LINK_TEXT",	
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "Ranking"
          }
      	},
      	{
      	  "placeholderField": "ADVANCED_URL",	
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "http://www.example.jp/ranking"
          }
      	}
      ],
      "placeholderType": "QUICKLINK"
    },
    {
      "feedItemAttribute": [
      	{
      	  "placeholderField": "LINK_TEXT",	
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "Support"
          }
      	},
      	{
      	  "placeholderField": "ADVANCED_URL",	
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "http://www.example.jp/support"
          }
      	}
      ],
      "placeholderType": "QUICKLINK"
    },
    {
      "feedItemAttribute": [
      	{
      	  "placeholderField": "LINK_TEXT",	
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "Coupon"
          }
      	},
      	{
      	  "placeholderField": "ADVANCED_URL",	
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "http://www.example.jp/coupon"
          }
      	}
      ],
      "placeholderType": "QUICKLINK"
    },
    {
      "feedItemAttribute": [
      	{
      	  "placeholderField": "LINK_TEXT",	
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "Special Sale"
          }
      	},
      	{
      	  "placeholderField": "ADVANCED_URL",	
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "http://www.example.jp/specialsale"
          }
      	}
      ],
      "placeholderType": "QUICKLINK"
    },
    {
      "feedItemAttribute": [
      	{
      	  "placeholderField": "LINK_TEXT",	
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "Point Information"
          }
      	},
      	{
      	  "placeholderField": "ADVANCED_URL",	
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "http://www.example.jp/point"
          }
      	}
      ],
      "placeholderType": "QUICKLINK"
    }
  ],
  "placeholderType": "QUICKLINK"
}
```
##### <Response Sample> [For QUICKLINK]
```json
{
    "errors": null,
    "rid": "7ed38ca199e760bb13a87ad42ecec3f7",
    "rval": {
        "values": [
            {
                "errors": null,
                "feedItem": {
                    "accountId": 11111111,
                    ...
                    "feedItemAttribute": [
                        {
                            "feedAttributeId": null,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "ADVANCED_URL",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "http://www.example.jp/sale"
                            }
                        },
                        {
                            "feedAttributeId": null,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "LINK_TEXT",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "Sale"
                            }
                        }
                    ],
                    "feedItemId": 10000001,
                    ...
                    "trademarkStatus": "NO_RESTRICTION"
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "feedItem": {
                    "accountId": 11111111,
                    ...
                    "feedItemAttribute": [
                        {
                            "feedAttributeId": null,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "ADVANCED_URL",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "http://www.example.jp/store"
                            }
                        },
                        {
                            "feedAttributeId": null,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "LINK_TEXT",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "Store List"
                            }
                        }
                    ],
                    "feedItemId": 10000002,
                    ...
                    "trademarkStatus": "NO_RESTRICTION"
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "feedItem": {
                    "accountId": 11111111,
                    ...
                    "feedItemAttribute": [
                        {
                            "feedAttributeId": null,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "ADVANCED_URL",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "http://www.example.jp/ranking"
                            }
                        },
                        {
                            "feedAttributeId": null,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "LINK_TEXT",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "Ranking"
                            }
                        }
                    ],
                    "feedItemId": 10000003,
                    ...
                    "trademarkStatus": "NO_RESTRICTION"
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "feedItem": {
                    "accountId": 11111111,
                    ...
                    "feedItemAttribute": [
                        {
                            "feedAttributeId": null,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "ADVANCED_URL",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "http://www.example.jp/support"
                            }
                        },
                        {
                            "feedAttributeId": null,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "LINK_TEXT",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "Support"
                            }
                        }
                    ],
                    "feedItemId": 10000004,
                    ...
                    "trademarkStatus": "NO_RESTRICTION"
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "feedItem": {
                    "accountId": 11111111,
                    ...
                    "feedItemAttribute": [
                        {
                            "feedAttributeId": null,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "ADVANCED_URL",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "http://www.example.jp/coupon"
                            }
                        },
                        {
                            "feedAttributeId": null,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "LINK_TEXT",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "Coupon"
                            }
                        }
                    ],
                    "feedItemId": 10000005,
                    ...
                    "trademarkStatus": "NO_RESTRICTION"
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "feedItem": {
                    "accountId": 11111111,
                    ...
                    "feedItemAttribute": [
                        {
                            "feedAttributeId": null,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "ADVANCED_URL",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "http://www.example.jp/specialsale"
                            }
                        },
                        {
                            "feedAttributeId": null,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "LINK_TEXT",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "Special Sale"
                            }
                        }
                    ],
                    "feedItemId": 10000006,
                    ...
                    "trademarkStatus": "NO_RESTRICTION"
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "feedItem": {
                    "accountId": 11111111,
                    ...
                    "feedItemAttribute": [
                        {
                            "feedAttributeId": null,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "ADVANCED_URL",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "http://www.example.jp/point"
                            }
                        },
                        {
                            "feedAttributeId": null,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "LINK_TEXT",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "Point Information"
                            }
                        }
                    ],
                    "feedItemId": 10000007,
                    ...
                    "trademarkStatus": "NO_RESTRICTION"
                },
                "operationSucceeded": true
            }
        ]
    }
}
```
##### <Request Sample> [For CALLEXTENSION]
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "feedItemAttribute": [
      	{
      	  "placeholderField": "CALL_PHONE_NUMBER",	
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "0120-45-6789"
          }
      	}
      ],
      "placeholderType": "CALLEXTENSION"
    }
  ],
  "placeholderType": "CALLEXTENSION"
}
```
##### <Response Sample> [For CALLEXTENSION]
```json
{
    "errors": null,
    "rid": "8ab8663bb20c4b334e11a84ccaa44bbe",
    "rval": {
        "values": [
            {
                "errors": null,
                "feedItem": {
                    "accountId": 11111111,
                    ...
                    "feedItemAttribute": [
                        {
                            "feedAttributeId": null,
                            "multipleFeedItemAttribute": null,
                            "placeholderField": "CALL_PHONE_NUMBER",
                            "simpleFeedItemAttribute": {
                                "feedAttributeValue": null,
                                "reviewFeedAttributeValue": "0120-45-6789"
                            }
                        }
                    ],
                    "feedItemId": 20000001,
                    ...
                    "trademarkStatus": null
                },
                "operationSucceeded": true
            }
        ]
    }
}
```
#### 1.5. Add Campaign Service
Before setting the campaign, add Campaign Service using CampaignService:add.
##### <Request Sample>
```json
{
  "accountId": 11111111,
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
      "campaignName": "test",
      "userStatus": "ACTIVE"
    }
  ]
}
```
##### <Response Sample>
```json
{
    "errors": null,
    "rid": "6737550a7103f943c831846d76e9c774",
    "rval": {
        "values": [
            {
                "campaign": {
                    "accountId": 11111111,
                    ...
                    "campaignId": 22222222,
                    "campaignName": "test",
                    ...
                    "userStatus": "ACTIVE"
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
``` 
#### 2. Setting to Campaign
FeedItem will be set to campaign using CampaignFeedService:set.   
For this example, QuickLink[No.1-4] and CallExtension[No.1] will be set to campaign.  
##### <Request Sample> [For QUICKLINK]
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "accountId": 11111111,
      "campaignFeed": [
        {
          "feedItemId": 10000001
        },
        {
          "feedItemId": 10000002
        },
        {
          "feedItemId": 10000003
        },
        {
          "feedItemId": 10000004
        }
      ],
      "campaignId": 22222222,
      "placeholderType": "QUICKLINK"
    }
  ]
}
```
##### <Response Sample> [For QUICKLINK]
```json
{
    "errors": null,
    "rid": "e38dac49d88bec66ba2816955393cd56",
    "rval": {
        "values": [
            {
                "campaignFeedList": {
                    "accountId": 11111111,
                    "campaignFeed": [
                        {
                            "accountId": 11111111,
                            "campaignId": 22222222,
                            "feedItemId": 10000001,
                            "placeholderType": "QUICKLINK"
                        },
                        {
                            "accountId": 11111111,
                            "campaignId": 22222222,
                            "feedItemId": 10000002,
                            "placeholderType": "QUICKLINK"
                        },
                        {
                            "accountId": 11111111,
                            "campaignId": 22222222,
                            "feedItemId": 10000003,
                            "placeholderType": "QUICKLINK"
                        },
                        {
                            "accountId": 11111111,
                            "campaignId": 22222222,
                            "feedItemId": 10000004,
                            "placeholderType": "QUICKLINK"
                        }
                    ],
                    "campaignId": 22222222,
                    "placeholderType": "QUICKLINK"
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
##### <Request Sample> [For CALLEXTENSION]
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "accountId": 11111111,
      "campaignFeed": [
        {
          "feedItemId": 20000001
        }
      ],
      "campaignId": 22222222,
      "placeholderType": "CALLEXTENSION"
    }
  ]
}
```
##### <Response Sample> [For CALLEXTENSION]
```json
{
    "errors": null,
    "rid": "9adfc69b06e9808c178f3c69d9eb54c0",
    "rval": {
        "values": [
            {
                "campaignFeedList": {
                    "accountId": 11111111,
                    "campaignFeed": [
                        {
                            "accountId": 11111111,
                            "campaignId": 22222222,
                            "feedItemId": 20000001,
                            "placeholderType": "CALLEXTENSION"
                        }
                    ],
                    "campaignId": 22222222,
                    "placeholderType": "CALLEXTENSION"
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
#### 2.5. Add AdGroupService
Before setting FeedItem to AdsGroup, add AdgroupService using AdGroupService:add.
##### <Request Sample>
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "adGroupName": "adgtest",
      "campaignId": 22222222,
      "userStatus": "ACTIVE"
    }
  ]
}
```
##### <Response Sample>
```json
{
    "errors": null,
    "rid": "b5bf6636ea9b2bff7fe9efa89bba2ed9",
    "rval": {
        "values": [
            {
                "adGroup": {
                    "accountId": 11111111,
                    "adGroupAdRotationMode": {
                        "adRotationMode": "OPTIMIZE"
                    },
                    "adGroupId": 33333333,
                    "adGroupName": "adgtest",
                    ...
                    "campaignId": 22222222,
                    "campaignName": "test",
                    ...
                    "userStatus": "ACTIVE"
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
#### 3.	Setting to Ad Group
FeedItem will be set to ad group using AdGroupFeedService:set.   
For this example, QuickLink[No.5] will be set to ad group.  
##### <Request Sample> [For QUICKLINK]
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "accountId": 11111111,
      "adGroupFeed": [
        {
          "feedItemId": 10000005,
          "placeholderType": "QUICKLINK"
        }
      ],
      "adGroupId": 33333333,
      "campaignId": 22222222,
      "placeholderType": "QUICKLINK"
    }
  ]
}
```
##### <Response Sample> [For QUICKLINK]
```json
{
    "errors": null,
    "rid": "7fb5317129e3d65be0b8ea0110988850",
    "rval": {
        "values": [
            {
                "adGroupFeedList": {
                    "accountId": 11111111,
                    "adGroupFeed": [
                        {
                            "accountId": 11111111,
                            "adGroupId": 33333333,
                            "campaignId": 22222222,
                            "feedItemId": 10000005,
                            "placeholderType": "QUICKLINK"
                        }
                    ],
                    "adGroupId": 33333333,
                    "campaignId": 22222222,
                    "placeholderType": "QUICKLINK"
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
##### <Request Sample> [For CALLEXTENSION]
```json  
{
  "accountId": 11111111,
  "operand": [
    {
      "accountId": 11111111,
      "adGroupFeed": [
        {
          "feedItemId": 20000001,
          "placeholderType": "CALLEXTENSION"
        }
      ],
      "adGroupId": 33333333,
      "campaignId": 22222222,
      "placeholderType": "CALLEXTENSION"
    }
  ]
}
```
##### <Response Sample> [For CALLEXTENSION]
```json
{
    "errors": null,
    "rid": "2d4b3c34a8a59091d095c0d3d1b413f2",
    "rval": {
        "values": [
            {
                "adGroupFeedList": {
                    "accountId": 11111111,
                    "adGroupFeed": [
                        {
                            "accountId": 11111111,
                            "adGroupId": 33333333,
                            "campaignId": 22222222,
                            "feedItemId": 20000001,
                            "placeholderType": "CALLEXTENSION"
                        }
                    ],
                    "adGroupId": 33333333,
                    "campaignId": 22222222,
                    "placeholderType": "CALLEXTENSION"
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
#### 4.	Change of FeedItem setting to Campaign
QuickLink setting to the campaign will be updated using CampaignFeedService:set, because the special sale has been decided to be held.  
For this example, QuickLink[No.1] will be deleted and QuickLink[No.6] will be set to campaign.  
##### <Request Sample> [For QUICKLINK]
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "accountId": 11111111,
      "campaignFeed": [
        {
          "feedItemId": 10000002
        },
	{
          "feedItemId": 10000003
        },
        {
          "feedItemId": 10000004
        },
	{
          "feedItemId": 10000006
        }
      ],
      "campaignId": 22222222,
      "placeholderType": "QUICKLINK"
    }
  ]
}
```
##### <Response Sample> [For QUICKLINK]
```json
{
    "errors": null,
    "rid": "a72a173721d4c8f0c7d6fe67ac1ad5ac",
    "rval": {
        "values": [
            {
                "campaignFeedList": {
                    "accountId": 11111111,
                    "campaignFeed": [
                        {
                            "accountId": 11111111,
                            "campaignId": 22222222,
                            "feedItemId": 10000002,
                            "placeholderType": "QUICKLINK"
                        },
                        {
                            "accountId": 11111111,
                            "campaignId": 22222222,
                            "feedItemId": 10000003,
                            "placeholderType": "QUICKLINK"
                        },
                        {
                            "accountId": 11111111,
                            "campaignId": 22222222,
                            "feedItemId": 10000004,
                            "placeholderType": "QUICKLINK"
                        },
                        {
                            "accountId": 11111111,
                            "campaignId": 22222222,
                            "feedItemId": 10000006,
                            "placeholderType": "QUICKLINK"
                        }
                    ],
                    "campaignId": 22222222,
                    "placeholderType": "QUICKLINK"
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
##### <Request Sample> [For CALLEXTENSION]
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "accountId": 11111111,
      "campaignFeed": [
        {
          "feedItemId": 20000001
        }
      ],
      "campaignId": 22222222,
      "placeholderType": "CALLEXTENSION"
    }
  ]
}
```
##### <Response Sample> [For CALLEXTENSION]
```json
{
    "errors": null,
    "rid": "839cdf63d2e593287eeee18936ba06df",
    "rval": {
        "values": [
            {
                "campaignFeedList": {
                    "accountId": 11111111,
                    "campaignFeed": [
                        {
                            "accountId": 11111111,
                            "campaignId": 22222222,
                            "feedItemId": 20000001,
                            "placeholderType": "CALLEXTENSION"
                        }
                    ],
                    "campaignId": 22222222,
                    "placeholderType": "CALLEXTENSION"
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
#### 5.	Change of FeedItem setting to Ad Group 
QuickLink setting to the ad group will be updated using AdGroupFeedService:set, because the coupon offer has ended.   
For this example, QuickLink[No.5] will be deleted and QuickLink[No.7] will be set toad group. 
##### <Request Sample>
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "accountId": 11111111,
      "adGroupFeed": [
        {
          "feedItemId": 10000007
        }
      ],
      "adGroupId": 33333333,
      "campaignId": 22222222,
      "placeholderType": "QUICKLINK"
    }
  ]
}
```
##### <Response Sample>
```json
{
    "errors": null,
    "rid": "161669b5ce3328f41f53acc1de380818",
    "rval": {
        "values": [
            {
                "adGroupFeedList": {
                    "accountId": 11111111,
                    "adGroupFeed": [
                        {
                            "accountId": 11111111,
                            "adGroupId": 33333333,
                            "campaignId": 22222222,
                            "feedItemId": 10000007,
                            "placeholderType": "QUICKLINK"
                        }
                    ],
                    "adGroupId": 33333333,
                    "campaignId": 22222222,
                    "placeholderType": "QUICKLINK"
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```

#### 6.	Canceling the CallExtension
The call center has been abolished, so the setting of CallExtension to the ad group will be deleted using AdGroupFeed:set. 
##### <Request Sample>
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "accountId": 11111111,
      "adGroupFeed": [
      ],
      "adGroupId": 33333333,
      "campaignId": 22222222,
      "placeholderType": "CALLEXTENSION"
    }
  ]
}
```
##### <Response Sample>
```json
{
    "errors": null,
    "rid": "738920396ca78aea0a05a45fa005c749",
    "rval": {
        "values": [
            {
                "adGroupFeedList": {
                    "accountId": 11111111,
                    "adGroupFeed": null,
                    "adGroupId": 33333333,
                    "campaignId": 22222222,
                    "placeholderType": "CALLEXTENSION"
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
