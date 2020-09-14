# 動的検索連動型広告
## 動的検索連動型広告とは
あらかじめ指定したサイトのコンテンツと関連性の高い検索キーワードに対して、広告のタイトルを自動的に生成して配信する広告です。<br>
詳しくは以下のヘルプをご参照ください。<br>
・<a href="https://ads-help.yahoo.co.jp/yahooads/ss/articledetail?lan=ja&aid=20994">動的検索連動型広告のメリットと仕組み</a>

## 動的検索連動型広告の入稿の流れ
動的検索連動型広告の入稿の流れは以下の通りです。
* ページフィードの入稿（ドメイン、ページURL、カスタムラベル※任意）
* キャンペーン作成（＋ドメイン全体またはページフィードを設定）
* 広告グループ作成（＋ターゲット設定）
* 広告作成
* （対象ウェブページのクロール後）配信<br>

※広告の審査が完了後、通常は1～3日、最長で2週程度で広告配信が開始されます。<br>

詳しくは以下のヘルプをご参照ください。<br>
・<a href="https://ads-help.yahoo.co.jp/yahooads/ss/articledetail?lan=ja&aid=28684">動的検索連動型広告の入稿の流れ</a>

#### 1.	フィードアイテム情報を追加
FeedService:addを使用して、フィードアイテム情報を追加します。以下の指定が必要です。<br>
* アカウントID（accountId）
* ドメイン（domain）
* フィード名（FeedName）
* FeedItem情報の種類（placeholderType）：動的検索連動型広告ページフィード（DYNAMIC_AD_FOR_SEARCH_PAGE_FEEDS）

##### ＜リクエストサンプル＞
```json
{
  "accountId": 111111,
  "operand": [
    {
      "domain": "http://example.yahoo.co.jp",
      "feedName": "商品list",
      "placeholderType": "DYNAMIC_AD_FOR_SEARCH_PAGE_FEEDS"
    }
  ]
}
```

##### ＜レスポンスサンプル＞
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
                    "feedName": "商品list",
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

#### 2.	ページフィードの入稿
次に、以下のようなページフィードアイテムcsvファイルを作成し、PageFeedItemService:uploadを使って、ページフィードアイテムをアップロードします。

|ページURL|カスタムラベル|
|---|---|
|http://example.yahoo.co.jp/1.html|Service;Japan;IT|
|http://example.yahoo.co.jp/2.html|Service;Japan;|

ファイルアップロードの際、以下の指定が必要です。<br>
* アップロードタイプ（NEW_OR_REPLACE:新規登録または、全て置き換える。MODIFY:既存のページフィードアイテムを更新）

##### ＜リクエストサンプル＞
https://ads-search.yahooapis.jp/api/v2/PageFeedItemService/upload?file=temp.csv&accountId=111111&uploadType=NEW_OR_REPLACE&feedId=123456

##### ＜レスポンスサンプル＞
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

#### 3.	キャンペーン作成
CampaignService:addを使用します。以下の指定が必要です。<br>
* キャンペーンのターゲティング設定情報（settingType）：動的検索連動型広告（DYNAMIC_ADS_FOR_SEARCH_SETTING）
* キャンペーンタイプ（type）：動的検索連動型広告用（DYNAMIC_ADS_FOR_SEARCH）

##### ＜リクエストサンプル＞
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

##### ＜レスポンスサンプル＞
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

#### 4.	広告グループ作成
AdGroupService:addを使用します。

##### ＜リクエストサンプル＞
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

##### ＜レスポンスサンプル＞
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

#### 5.	広告作成
AdGroupAdService:addを使用します。以下の指定が必要です。<br>
* 広告タイプ（ad:adType）：動的検索連動型広告（DYNAMIC_SEARCH_LINKED_AD）
* 説明文（ad:description1）：自由記述　※1のみの指定。

##### ＜リクエストサンプル＞
```json
{
  "accountId": 111111,
  "operand": [
    {
      "ad": {
        "adType": "DYNAMIC_SEARCH_LINKED_AD",        
        "description1": "広告の説明文01",
        "devicePreference": "SMART_PHONE"
      },
      "adGroupId": 333333,
      "adName": "広告名01",
      "campaignId": 222222,
      "userStatus": "ACTIVE"
    }
  ]
}
```

##### ＜レスポンスサンプル＞
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
                        "description1": "広告の説明文01",
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
                    "adName": "広告名01",
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
