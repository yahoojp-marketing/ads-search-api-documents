# Ad display asset
## What is “Ad display asset”?
\* This best practice page is for the new method to be released in Spring, 2022.
			
<A href="https://ads-help.yahoo-net.jp/s/article/H000045056?language=en_US">Ad display asset</a> is a function of displaying additional information such as a link to other URL page or phone number to Search Ads.   
    
There are 4 features for Ad display asset:  
* "QuickLink" (Quick link asset)
* "CallExtension" (Call asset)  
* “CALLOUT” (Callout asset)
* “STRUCTURED_SNIPPET” (Category snippet asset)
  
There are 2 advantages from using Ad display asset.    
1. Ad spaces become larger and increase the visibility. This will raise the click rate.
2. Can easily access to the page that user desires. This will raise the convenience.

## How to operate through Search Ads API
To display ads with Ad display asset, use the 3 services below from Search Ads API.  
##### 1. AssetService 
In AssetService, you can retrieve, add and update Asset Information.  
Asset Information is a component such as text, link URL, and phone number to be displayed as Ad display asset.
  
##### 2. CampaignAssetService
In CampaignAssetService, you can set the added Asset Information to campaign, and retrieve the Asset Information that is set to campaign. 
  
##### 3. AdGroupAssetService
InAdGroupAssetService, you can set the added Asset Information to ad group, and retrieve the Asset Information that is set to ad group. 
  
## Examples
Company A is planning to add the below Ad display asset through Search Ads API for their sales promotion.
  
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

#### 1.	Adding Asset Information
First, add an Asset Information to Search Ads account using AssetService:add.  
In this example, each Ad display asset will be added to the account of company A (ID: 11111111).  
##### \<Request Sample> [For QUICKLINK]
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "assetData": {
        "type": "QUICKLINK",
        "quickLinkAsset": {
          "linkText": "Sale"
        }
      },
      "finalUrl": "http://www.example.jp/sale"
    },
    {
      "assetData": {
        "type": "QUICKLINK",
        "quickLinkAsset": {
          "linkText": "Store List"
        }
      },
      "finalUrl": "http://www.example.jp/store"
    },
    {
      "assetData": {
        "type": "QUICKLINK",
        "quickLinkAsset": {
          "linkText": "Ranking"
        }
      },
      "finalUrl": "http://www.example.jp/ranking"
    },
    {
      "assetData": {
        "type": "QUICKLINK",
        "quickLinkAsset": {
          "linkText": "Support"
        }
      },
      "finalUrl": "http://www.example.jp/support"
    },
    {
      "assetData": {
        "type": "QUICKLINK",
        "quickLinkAsset": {
          "linkText": "Coupon"
        }
      },
      "finalUrl": "http://www.example.jp/coupon"
    },
    {
      "assetData": {
        "type": "QUICKLINK",
        "quickLinkAsset": {
          "linkText": "Special Sale"
        }
      },
      "finalUrl": "http://www.example.jp/specialsale"
    },
    {
      "assetData": {
        "type": "QUICKLINK",
        "quickLinkAsset": {
          "linkText": "Point Information"
        }
      },
      "finalUrl": "http://www.example.jp/point"
    }
  ]
}

```
##### \<Response Sample> [For QUICKLINK]
```json
{
  "errors": null,
  "rid": "xxxxxxxxxxxxxxxxxxxx",
  "rval": {
    "values": [
      {
        "errors": null,
        "asset": {
          "accountId": 11111111,
          "assetId": 30001,
          "assetTrackId": 0,
          "assetData": {
            "type": "QUICKLINK",
            "quickLinkAsset": {
              "linkText": "Sale",
              "reviewLinkText": null,
              "description1": null,
              "reviewDescription1": null,
              "description2": null,
              "reviewDescription2": null,
              "startDate": null,
              "endDate": null,
              "schedules": null
            },
            "callAsset": null,
            "calloutAsset": null,
            "structuredSnippetAsset": null
          },
          "approvalStatus": "REVIEW",
          "disapprovalReasonCodes": null,
          "invalidedTrademarks": null,
          "trademarkStatus": "NO_RESTRICTION",
          "customParameters": null,
          "reviewCustomParameters": null,
          "smartphoneFinalUrl": null,
          "reviewSmartphoneFinalUrl": null,
          "finalUrl": "http://www.example.jp/sale",
          "reviewFinalUrl": null,
          "trackingUrl": null,
          "reviewTrackingUrl": null
        },
        "operationSucceeded": true
      },
      {
        "errors": null,
        "asset": {
          "accountId": 11111111,
          "assetId": 30002,
          "assetTrackId": 0,
          ...
          "reviewFinalUrl": null,
          "trackingUrl": null,
          "reviewTrackingUrl": null
        },
        "operationSucceeded": true
      }
    ]
  }
}

```
##### \<Request Sample> [For CALLEXTENSION]
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "assetData": {
        "type": "CALL",
        "callAsset": {
          "phoneNumber": "0120-45-6789"
        }
      }
    }
  ]
}
```
##### \<Response Sample> [For CALLEXTENSION]
```json
{
  "errors": null,
  "rid": "xxxxxxxxxxxxxxxxxxxx",
  "rval": {
    "values": [
      {
        "errors": null,
        "asset": {
          "accountId": 11111111,
          "assetId": 30008,
          "assetTrackId": 0,
          "assetData": {
            "type": "CALL",
            "quickLinkAsset": null,
            "callAsset": {
              "phoneNumber": "0120-45-6789",
              "reviewPhoneNumber": null,
              "schedules": null
            },
            "calloutAsset": null,
            "structuredSnippetAsset": null
          },
          "approvalStatus": "REVIEW",
          "disapprovalReasonCodes": null,
          "invalidedTrademarks": null,
          "trademarkStatus": null,
          "customParameters": null,
          "reviewCustomParameters": null,
          "smartphoneFinalUrl": null,
          "reviewSmartphoneFinalUrl": null,
          "finalUrl": null,
          "reviewFinalUrl": null,
          "trackingUrl": null,
          "reviewTrackingUrl": null
        },
        "operationSucceeded": true
      }
    ]
  }
}
```

#### 1.5. Add a Campaign
Before setting the campaign, add a Campaign using CampaignService:add.
##### \<Request Sample>
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "biddingStrategyConfiguration": {
        "biddingScheme": {
          "biddingStrategyType": "CPC",
          "cpcBiddingScheme": {
            "enhancedCpcEnabled": "TRUE"
          }
        }
      },
      "budget": {
        "amount": 100,
        "budgetPeriod": "DAILY"
      },
      "campaignName": "Campaign Test",
      "userStatus": "ACTIVE"
    }
  ]
}
```
##### \<Response Sample>
```json
{
  "errors": null,
  "rid": "xxxxxxxxxxxxxxxxxxxx",
  "rval": {
    "values": [
      {
        "campaign": {
          "accountId": 11111111,
          "appId": null,
          "appStore": null,
          "biddingStrategyConfiguration": {
            "biddingScheme": {
              "biddingStrategyType": "CPC",
              "cpcBiddingScheme": {
                "enhancedCpcEnabled": "TRUE"
              },
              "targetCpaBiddingScheme": null,
              "targetRoasBiddingScheme": null,
              "maximizeClicksBiddingScheme": null,
              "targetImpressionShareScheme": null,
              "maximizeConversionsBiddingScheme": null,
              "maximizeConversionValueBiddingScheme": null
            },
            "biddingStrategyId": null,
            "biddingStrategyName": null,
            "biddingStrategySource": "CAMPAIGN"
          },
          "biddingStrategyFailedReason": null,
          "budget": {
            "amount": 100,
            "budgetPeriod": "DAILY"
          },
          "campaignId": 22222222,
          "campaignName": "Test Test Test1",
          "campaignTrackId": 0,
          "conversionOptimizerEligibility": "DISABLE",
          "customParameters": null,
          "endDate": "20371231",
          "failedBiddingStrategyConfiguration": null,
          "labels": null,
          "servingStatus": "SERVING",
          "settings": [
            {
              "dynamicAdsForSearchSetting": null,
              "geoTargetTypeSetting": {
                "negativeGeoTargetType": "LOCATION_OF_PRESENCE",
                "positiveGeoTargetType": "DONT_CARE"
              },
              "settingType": "GEO_TARGET_TYPE_SETTING",
              "targetingSetting": null
            },
            {
              "dynamicAdsForSearchSetting": null,
              "geoTargetTypeSetting": null,
              "settingType": "TARGET_LIST_SETTING",
              "targetingSetting": {
                "targetAll": "ACTIVE"
              }
            }
          ],
          "startDate": "20220125",
          "trackingUrl": null,
          "type": "STANDARD",
          "urlReviewData": {
            "disapprovalReasonCodes": null,
            "disapprovalReviewUrl": null,
            "inReviewUrl": null,
            "urlApprovalStatus": "NONE"
          },
          "userStatus": "ACTIVE",
          "createdDate": "20220125"
        },
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}

``` 
#### 2. Setting to Campaign
Next, set the added Asset Information to campaign using CampaignAssetService:replace.  
In this example, QuickLink[No.1-4] and CallExtension[No.1] will be set to campaign.
##### \<Request Sample> [For QUICKLINK]
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "campaignAssets": [
        {
          "accountId": null,
          "campaignId": null,
          "assetId": 30001,
          "type": null,
          "userStatus": "ACTIVE"
        },
        {
          "accountId": null,
          "campaignId": null,
          "assetId": 30002,
          "type": null,
          "userStatus": "ACTIVE"
        },
        {
          "accountId": null,
          "campaignId": null,
          "assetId": 30003,
          "type": null,
          "userStatus": "ACTIVE"
        },
        {
          "accountId": null,
          "campaignId": null,
          "assetId": 30004,
          "type": null,
          "userStatus": "ACTIVE"
        }
      ],
      "campaignId": 22222222,
      "type": "QUICKLINK"
    }
  ]
}

```
##### \<Response Sample> [For QUICKLINK]
```json
{
  "errors": null,
  "rid": "xxxxxxxxxxxxxxxxxxxx",
  "rval": {
    "values": [
      {
        "campaignAssets": [
          {
            "accountId": 11111111,
            "campaignId": 22222222,
            "assetId": 30001,
            "type": "QUICKLINK",
            "userStatus": "ACTIVE"
          },
          {
            "accountId": 11111111,
            "campaignId": 22222222,
            "assetId": 30002,
            "type": "QUICKLINK",
            "userStatus": "ACTIVE"
          },
          {
            "accountId": 11111111,
            "campaignId": 22222222,
            "assetId": 30003,
            "type": "QUICKLINK",
            "userStatus": "ACTIVE"
          },
          {
            "accountId": 11111111,
            "campaignId": 22222222,
            "assetId": 30004,
            "type": "QUICKLINK",
            "userStatus": "ACTIVE"
          }
        ],
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}
```
##### \<Request Sample> [For CALLEXTENSION]
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "campaignAssets": [
        {
          "accountId": null,
          "campaignId": null,
          "assetId": 30008,
          "type": null,
          "userStatus": "ACTIVE"
        }
      ],
      "campaignId": 22222222,
      "type": "CALL"
    }
  ]
}
```
##### \<Response Sample> [For CALLEXTENSION]
```json
{
  "errors": null,
  "rid": "xxxxxxxxxxxxxxxxxxxx",
  "rval": {
    "values": [
      {
        "campaignAssets": [
          {
            "accountId": 11111111,
            "campaignId": 22222222,
            "assetId": 30008,
            "type": "CALL",
            "userStatus": "ACTIVE"
          }
        ],
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}
```
#### 2.5. Add Ad Group
Before setting an Asset Information to Ad Group, add an Ad Group using AdGroupService:add.
##### \<Request Sample>
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
##### \<Response Sample>
```json
{
  "errors": null,
  "rid": "xxxxxxxxxxxxxxxxxxxx",
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
          "adGroupTrackId": 0,
          "bid": {
            "bidSource": "ADGROUP",
            "cpc": 1
          },
          "campaignId": 22222222,
          "campaignName": "campaigntest",
          "campaignTrackId": 99999999,
          "customParameters": null,
          "labels": null,
          "settings": {
            "criterionType": "TARGET_LIST",
            "targetingSetting": {
              "targetAll": "ACTIVE"
            }
          },
          "targetRoasOverride": null,
          "targetCpaOverride": null,
          "trackingUrl": null,
          "urlReviewData": {
            "disapprovalReasonCodes": null,
            "disapprovalReviewUrl": null,
            "inReviewUrl": null,
            "urlApprovalStatus": "NONE"
          },
          "userStatus": "ACTIVE",
          "createdDate": "20220125"
        },
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}
```
#### 3.	Setting to Ad Group
Next, set the added Asset Information to Ad Group using AdGroupAssetService:replace.  
In this example, QuickLink[No.5] will be set to Ad Group.
##### \<Request Sample> [For QUICKLINK]
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "adGroupAssets": [
        {
          "accountId": 11111111,
          "assetId": 30005,
          "userStatus": "ACTIVE"
        }
      ],
      "adGroupId": 33333333,
      "campaignId": 22222222,
      "type": "QUICKLINK"
    }
  ]
}
```
##### \<Response Sample> [For QUICKLINK]
```json
{
  "errors": null,
  "rid": "xxxxxxxxxxxxxxxxxxxx",
  "rval": {
    "values": [
      {
        "adGroupAssets": [
          {
            "accountId": 11111111,
            "adGroupId": 33333333,
            "campaignId": 22222222,
            "assetId": 30005,
            "type": "QUICKLINK",
            "userStatus": "ACTIVE"
          }
        ],
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}
```
##### \<Request Sample> [For CALLEXTENSION]
```json  
{
  "accountId": 11111111,
  "operand": [
    {
      "adGroupAssets": [
        {
          "accountId": 11111111,
          "assetId": 30008,
          "userStatus": "ACTIVE"
        }
      ],
      "adGroupId": 33333333,
      "campaignId": 22222222,
      "type": "CALL"
    }
  ]
}
```
##### \<Response Sample> [For CALLEXTENSION]
```json
{
  "errors": null,
  "rid": "xxxxxxxxxxxxxxxxxxxx",
  "rval": {
    "values": [
      {
        "adGroupAssets": [
          {
            "accountId": 11111111,
            "adGroupId": 33333333,
            "campaignId": 22222222,
            "assetId": 30008,
            "type": "CALL",
            "userStatus": "ACTIVE"
          }
        ],
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}
```
#### 4.	Changing the Campaign's Asset Information
For the special sale has been decided to be held, the Campaign's QuickLink will be updated using CampaignAssetService:replace.  
In this example, QuickLink[No.1] will be deleted and QuickLink[No.6] will be set to the campaign.   
\* Updates will always be overwritten, so the Asset Information should be updated including the parts that does not need any updates.  
\* In order to delete the Asset Information, update the campaignAssets with empty information.  
##### \<Request Sample> [For QUICKLINK]
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "campaignAssets": [
        {
          "accountId": null,
          "campaignId": null,
          "assetId": 30002,
          "type": null,
          "userStatus": "ACTIVE"
        },
        {
          "accountId": null,
          "campaignId": null,
          "assetId": 30003,
          "type": null,
          "userStatus": "ACTIVE"
        },
        {
          "accountId": null,
          "campaignId": null,
          "assetId": 30004,
          "type": null,
          "userStatus": "ACTIVE"
        },
        {
          "accountId": null,
          "campaignId": null,
          "assetId": 30006,
          "type": null,
          "userStatus": "ACTIVE"
        }
      ],
      "campaignId": 22222222,
      "type": "QUICKLINK"
    }
  ]
}
```
##### \<Response Sample> [For QUICKLINK]
```json
{
  "errors": null,
  "rid": "xxxxxxxxxxxxxxxxxxxx",
  "rval": {
    "values": [
      {
        "campaignAssets": [
          {
            "accountId": 11111111,
            "campaignId": 22222222,
            "assetId": 30002,
            "type": "QUICKLINK",
            "userStatus": "ACTIVE"
          },
          {
            "accountId": 11111111,
            "campaignId": 22222222,
            "assetId": 30003,
            "type": "QUICKLINK",
            "userStatus": "ACTIVE"
          },
          {
            "accountId": 11111111,
            "campaignId": 22222222,
            "assetId": 30004,
            "type": "QUICKLINK",
            "userStatus": "ACTIVE"
          },
          {
            "accountId": 11111111,
            "campaignId": 22222222,
            "assetId": 30006,
            "type": "QUICKLINK",
            "userStatus": "ACTIVE"
          }
        ],
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}
```

#### 5.	Changing the Ad Group's Asset Information 
For the coupon offer has ended, the asset will be changed to a link to point campaign page using AdGroupAssetService:replace. 
In this example, QuickLink[No.5] will be deleted and QuickLink[No.7] will be set to Ad Group.
##### \<Request Sample>
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "adGroupAssets": [
        {
          "accountId": 11111111,
          "assetId": 30007,
          "userStatus": "ACTIVE"
        }
      ],
      "adGroupId": 33333333,
      "campaignId": 22222222,
      "type": "QUICKLINK"
    }
  ]
}

```
##### \<Response Sample>
```json
{
  "errors": null,
  "rid": "xxxxxxxxxxxxxxxxxxxx",
  "rval": {
    "values": [
      {
        "adGroupAssets": [
          {
            "accountId": 11111111,
            "adGroupId": 33333333,
            "campaignId": 22222222,
            "assetId": 30007,
            "type": "QUICKLINK",
            "userStatus": "ACTIVE"
          }
        ],
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}
```

#### 6.	Canceling the CallExtension
The call center has been abolished, so the setting of CallExtension to the ad group will be deleted using AdGroupAssetService:replace. 
##### \<Request Sample>
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "adGroupAssets": [],
      "adGroupId": 33333333,
      "campaignId": 22222222,
      "type": "CALL"
    }
  ]
}
```
##### \<Response Sample>
```json
{
  "errors": null,
  "rid": "xxxxxxxxxxxxxxxxxxxx",
  "rval": {
    "values": [
      {
        "adGroupAssets": null,
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}
```
#### 7.	Changing the setting status between Campaign and Assets
In order to pause the setting status of QuickLink[No.2], change the userStatus between Campaign and Asset using CampaignAssetService:set.
##### \<Request Sample>
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "accountId": 11111111,
      "campaignId": 22222222,
      "assetId": 30002,
      "type": "QUICKLINK",
      "userStatus": "PAUSED"
    }
  ]
}
```
##### \<Response Sample>
```json
{
  "errors": null,
  "rid": "xxxxxxxxxxxxxxxxxxxx",
  "rval": {
    "values": [
      {
        "campaignAsset": {
          "accountId": 11111111,
          "campaignId": 22222222,
          "assetId": 30002,
          "type": "QUICKLINK",
          "userStatus": "PAUSED"
        },
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}
```
