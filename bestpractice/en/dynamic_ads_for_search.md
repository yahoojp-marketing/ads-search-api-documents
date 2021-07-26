# Dynamic Ads for Search
## Whats is Dynamic Ads for Search?
Ads with the title automatically generated.<br>
For details, refer to the help below.<br>
・<a href="https://ads-help.yahoo.co.jp/yahooads/ss/articledetail?lan=en&aid=15375">Benefits of Dynamic Ads for Search and how it works</a>

## Create Dynamic Ads for Search
You can create Dynamic Ads for Search with following flow.
* Add Page Feed (Domain, Page URL, Custom Label※opt)
* Create Campaign (&Set up Page Feeds)
* Greate Ad Groups (&Targeting Settings)
* Create Ads
* (After crawling the targeted URL) Ad Delivery<br>

Once the ad has been reviewed, ad delivery usually begins in 1-3 days, up to a maximum of 2 weeks.<br>

For details, refer to the help below.<br>
・<a href="https://ads-help.yahoo.co.jp/yahooads/ss/articledetail?lan=en&aid=283">Create Dynamic Ads for Search</a>

#### 1.	Add feed item information
Add feed item information with FeedService:add. Specify the following.<br>
* accountId
* domain
* FeedName
* placeholderType:DYNAMIC_AD_FOR_SEARCH_PAGE_FEEDS

##### Request sample
```json
{
  "accountId": 111111,
  "operand": [
    {
      "domain": "http://example.yahoo.co.jp",
      "feedName": "Product list",
      "placeholderType": "DYNAMIC_AD_FOR_SEARCH_PAGE_FEEDS"
    }
  ]
}
```

##### Response sample
```json
{
    "errors": null,
    "rid": "5ff2b9a29f9a8b4ef735d83219ff7b15",
    "rval": {
        "values": [
            {
                "errors": null,
                "feed": {
                    "accountId": 111111,
                    "domain": "http://example.yahoo.co.jp",
                    "feedAttribute": [],
                    "feedId": 123456,
                    "feedName": "Product list",
                    "feedTrackId": 0,
                    "placeholderType": "DYNAMIC_AD_FOR_SEARCH_PAGE_FEEDS"
                },
                "operationSucceeded": true
            }
        ]
    }
}
```
<br>

#### 2.	Upload page feed
Create the following csv file and upload page feed with PageFeedItemService:upload.

|Page URL|Custom Label|
|---|---|
|http://example.yahoo.co.jp/1.html|Service;Japan;IT|
|http://example.yahoo.co.jp/2.html|Service;Japan;|

Specify the following.<br>
* uploadType (NEW_OR_REPLACE or MODIFY)

##### Request sample
https://ads-search.yahooapis.jp/api/v5/PageFeedItemService/upload?file=temp.csv&accountId=111111&uploadType=NEW_OR_REPLACE&feedId=123456

##### Response sample
```json
{
    "errors": null,
    "rid": "12e7bab1b86851a34f625312f3caf46f",
    "rval": {
        "values": [
            {
                "errors": null,
                "uploadJob": {
                    "accountId": 111111,
                    "endDate": null,
                    "errorCount": null,
                    "feedIds": [
                        123456
                    ],
                    "jobId": 7700,
                    "progress": null,
                    "startDate": null,
                    "uploadJobStatus": null
                },
                "operationSucceeded": true
            }
        ]
    }
}
```
<br>

#### 3.	Add Campaign
Add Campaign with CampaignService:add. Specify the following.<br>
* settings:settingType:DYNAMIC_ADS_FOR_SEARCH_SETTING
* type:DYNAMIC_ADS_FOR_SEARCH

##### Request sample
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
      "campaignName": "auto_campaign_01",
      "settings": [
        {
          "dynamicAdsForSearchSetting": {
            "feedIds": [
              123456
            ]
          },
          "settingType": "DYNAMIC_ADS_FOR_SEARCH_SETTING",
          "targetingSetting": {
            "targetAll": "ACTIVE"
          }
        }
      ],
      "type": "DYNAMIC_ADS_FOR_SEARCH",
      "userStatus": "ACTIVE"
    }
  ]
}
```

##### Response sample
```json
{
    "errors": null,
    "rid": "25263345ef84ad5aa9532accfff25656",
    "rval": {
        "values": [
            {
                "campaign": {
                    "accountId": 111111,
                    "appId": null,
                    "appStore": null,
                    "biddingStrategyConfiguration": {
                        "biddingScheme": {
                            "biddingStrategyType": "MANUAL_CPC",
                            "manualCpcBiddingScheme": {
                                "enhancedCpcEnabled": "TRUE"
                            },
                            "targetCpaBiddingScheme": null,
                            "targetRoasBiddingScheme": null,
                            "targetSpendBiddingScheme": null
                        },
                        "biddingStrategyId": null,
                        "biddingStrategyName": null,
                        "biddingStrategySource": "CAMPAIGN",
                        "biddingStrategyType": "MANUAL_CPC"
                    },
                    "biddingStrategyFailedReason": null,
                    "budget": {
                        "amount": 100,
                        "budgetPeriod": "DAILY"
                    },
                    "campaignId": 222222,
                    "campaignName": "auto_campaign_01",
                    "campaignTrackId": 0,
                    "conversionOptimizerEligibility": "DISABLE",
                    "customParameters": null,
                    "endDate": "20371231",
                    "failedBiddingStrategyConfiguration": null,
                    "labels": null,
                    "servingStatus": "SERVING",
                    "settings": [
                        {
                            "dynamicAdsForSearchSetting": {
                                "feedIds": [
                                    123456
                                ]
                            },
                            "geoTargetTypeSetting": null,
                            "settingType": "DYNAMIC_ADS_FOR_SEARCH_SETTING",
                            "targetingSetting": null
                        },
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
                    "startDate": "20200908",
                    "trackingUrl": null,
                    "type": "DYNAMIC_ADS_FOR_SEARCH",
                    "urlReviewData": {
                        "disapprovalReasonCodes": null,
                        "disapprovalReviewUrl": null,
                        "inReviewUrl": null,
                        "urlApprovalStatus": "NONE"
                    },
                    "userStatus": "ACTIVE"
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
<br>

#### 4.	Add ads group
Add ads group with AdGroupService:add.

##### Request sample
```json
{
  "accountId": 111111,
  "operand": [
    {
      "adGroupName": "auto_adgroup_01",
      "campaignId": 222222,
      "userStatus": "ACTIVE"
    }
  ]
}
```

##### Response sample
```json
{
    "errors": null,
    "rid": "84cdb8486a734150afcad28a8fb06aef",
    "rval": {
        "values": [
            {
                "adGroup": {
                    "accountId": 111111,
                    "adGroupAdRotationMode": {
                        "adRotationMode": "OPTIMIZE"
                    },
                    "adGroupId": 333333,
                    "adGroupName": "auto_adgroup_01",
                    "adGroupTrackId": 0,
                    "bid": {
                        "bidSource": "ADGROUP",
                        "maxCpc": 1
                    },
                    "campaignId": 222222,
                    "campaignName": "auto_campaign_01",
                    "campaignTrackId": 100000,
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
                    "userStatus": "ACTIVE"
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
<br>

#### 5.	Add Ads
Add Ads with AdGroupAdService:add. Specify the following.<br>
* ad:adType:DYNAMIC_SEARCH_LINKED_AD
* ad:description1: (Free)　※only description1

##### Request sample
```json
{
  "accountId": 111111,
  "operand": [
    {
      "ad": {
        "adType": "DYNAMIC_SEARCH_LINKED_AD",        
        "description1": "Ad description 01",
        "devicePreference": "SMART_PHONE"
      },
      "adGroupId": 333333,
      "adName": "Ad name 01",
      "campaignId": 222222,
      "userStatus": "ACTIVE"
    }
  ]
}
```

##### Response sample
```json
{
    "errors": null,
    "rid": "54d647d2f59a14a082de68d381cd9699",
    "rval": {
        "values": [
            {
                "adGroupAd": {
                    "accountId": 111111,
                    "ad": {
                        "adType": "DYNAMIC_SEARCH_LINKED_AD",
                        "additionalAdvancedMobileUrls": [],
                        "additionalAdvancedUrls": [],
                        "advancedMobileUrl": null,
                        "advancedUrl": null,
                        "appAd": null,
                        "customParameters": null,
                        "description1": "Ad description 01",
                        "devicePreference": null,
                        "displayUrl": null,
                        "extendedTextAd": null,
                        "headline1": null,
                        "textAd2": null,
                        "trackingUrl": null,
                        "url": null
                    },
                    "adGroupId": 333333,
                    "adGroupName": "auto_adgroup_01",
                    "adGroupTrackId": 200000,
                    "adId": 444444,
                    "adName": "Ad name 01",
                    "adTrackId": 0,
                    "approvalStatus": "REVIEW",
                    "campaignId": 222222,
                    "campaignName": "auto_campaign_01",
                    "campaignTrackId": 100000,
                    "disapprovalReasonCodes": null,
                    "feedId": null,
                    "invalidedTrademarks": null,
                    "labels": null,
                    "trademarkStatus": "NO_RESTRICTION",
                    "userStatus": "ACTIVE"
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
