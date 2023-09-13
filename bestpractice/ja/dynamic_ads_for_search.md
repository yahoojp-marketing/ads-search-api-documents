# 動的検索連動型広告
## 動的検索連動型広告とは
あらかじめ指定したサイトのコンテンツと関連性の高い検索キーワードに対して、広告のタイトルを自動的に生成して配信する広告です。<br>
詳しくは以下のヘルプをご参照ください。<br>
・<a href="https://ads-help.yahoo-net.jp/s/article/H000044549?language=ja">動的検索連動型広告のメリットと仕組み</a>

## 動的検索連動型広告の入稿の流れ
動的検索連動型広告の入稿の流れは以下の通りです。
* ページフィードの入稿（ドメイン、ページURL、カスタムラベル※任意）
* キャンペーン作成（＋ドメイン全体またはページフィードを設定）
* 広告グループ作成（＋ターゲット設定）
* 広告作成
* （対象ウェブページのクロール後）配信<br>

※広告の審査が完了後、通常は1～3日、最長で2週程度で広告配信が開始されます。<br>

詳しくは以下のヘルプをご参照ください。<br>
・<a href="https://ads-help.yahoo-net.jp/s/article/H000044590?language=ja">動的検索連動型広告の入稿の流れ</a>

#### 1.	フィードアイテム情報を追加
PageFeedAssetSetService:addを使用して、フィードアイテム情報を追加します。以下の指定が必要です。<br>
* アカウントID（accountId）<br>
* ドメイン（domain）<br>
* フィード名（pageFeedAssetSetName）<br>

##### ＜リクエストサンプル＞
```json
{
  "accountId": 111111,
  "operand": [
    {
      "accountId": 111111,
      "domain": "http://example.yahoo.co.jp",
      "pageFeedAssetSetName": "商品list"
    }
  ]
}
```

##### ＜レスポンスサンプル＞
```json
{
    "errors": null,
    "rid": "1234567890123456ascdefghijklmno",
    "rval": {
        "values": [
            {
                "errors": null,
                "pageFeedAssetSet": {
                    "accountId": 111111,
                    "pageFeedAssetSetId": 12345,
                    "pageFeedAssetSetName": "商品list",
                    "domain": "http://example.yahoo.co.jp"
                },
                "operationSucceeded": true
            }
        ]
    }
}
```
<br>

#### 2.	ページフィードの入稿
次に、以下のようなページフィードアイテムcsvファイルを作成し、PageFeedAssetService:uploadを使って、ページフィードアイテムをアップロードします。

|ページURL|カスタムラベル|
|---|---|
|http://example.yahoo.co.jp/1.html|Service;Japan;IT|
|http://example.yahoo.co.jp/2.html|Service;Japan;|

※ページフィードアイテムcsvファイルのテンプレートは、管理画面からダウンロードもできます。<br>
　詳しくは以下のヘルプをご参照ください。<br>
　<a href="https://ads-help.yahoo-net.jp/s/article/H000044706?language=ja">ページフィードの作成方法</a>

ファイルアップロードの際、クエリパラメータに以下の指定が必要です。<br>
*　accountId <br>
*　pageFeedAssetSetId <br>
*　uploadType（NEW_OR_REPLACE:新規登録または、全て置き換える。MODIFY:既存のページフィードアイテムを更新） <br>
リクエストbody に Content-Type: multipart/form-data 形式でファイル本文を指定します。<br>
ご参考：リファレンス<br>
　　　　https://ads-developers.yahoo.co.jp/reference/ads-search-api/v10/PageFeedAssetService/upload/

##### ＜リクエストサンプル＞
https://ads-search.yahooapis.jp/api/v10/PageFeedAssetService/upload?file=temp.csv&accountId=111111&uploadType=NEW_OR_REPLACE&pageFeedAssetSetId=12345

##### ＜レスポンスサンプル＞
```json
{
    "errors": null,
    "rid": "1234567890123456ascdefghijklmnp",
    "rval": {
        "values": [
            {
                "errors": null,
                "uploadJob": {
                    "accountId": 111111,
                    "jobId": 3450,
                    "pageFeedAssetSetId": 12345,
                    "uploadJobStatus": "IN_PROGRESS",
                    "progress": 0,
                    "errorCount": null,
                    "startDate": null,
                    "endDate": null
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
      "accountId": 111111,
      "biddingStrategyConfiguration": {
        "biddingScheme": {
          "biddingStrategyType": "CPC",
          "cpcBiddingScheme": {
            "enhancedCpcEnabled": "TRUE"
          }
        },
        "biddingStrategySource": "CAMPAIGN"
      },
      "budget": {
        "amount": 100
      },
      "campaignName": "auto_campaign_01",
      "settings": [
        {
          "dynamicAdsForSearchSetting": {
            "pageFeedAssetSetIds": [
              12345
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
    "rid": "1234567890123456ascdefghijklmnq",
    "rval": {
        "values": [
            {
                "campaign": {
                    "accountId": 111111,
                    "appId": null,
                    "appOsType": null,
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
                        "portfolioBiddingId": null,
                        "portfolioBiddingName": null,
                        "biddingStrategySource": "CAMPAIGN"
                    },
                    "biddingStrategyFailedReason": null,
                    "budget": {
                        "amount": 100
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
                                "feedIds": null,
                                "pageFeedAssetSetIds": [
                                    12345
                                ],
                                "domain": null,
                                "dasUseUrlsType": "USE_SUPPLIED_URLS_ONLY"
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
                    "startDate": "20230329",
                    "trackingUrl": null,
                    "type": "DYNAMIC_ADS_FOR_SEARCH",
                    "urlReviewData": {
                        "disapprovalReasonCodes": null,
                        "disapprovalReviewUrl": null,
                        "inReviewUrl": null,
                        "urlApprovalStatus": "NONE"
                    },
                    "userStatus": "ACTIVE",
                    "createdDate": "20230329"
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
    "rid": "1234567890123456ascdefghijklmnr",
    "rval": {
        "values": [
            {
                "adGroup": {
                    "accountId": 111111,
                    "biddingStrategyConfiguration": {
                        "biddingScheme": {
                            "campaignBiddingStrategyType": "CPC",
                            "cpcBiddingScheme": {
                                "cpc": 1
                            },
                            "targetCpaBiddingScheme": null,
                            "targetRoasBiddingScheme": null,
                            "maximizeConversionsBiddingScheme": null,
                            "maximizeConversionValueBiddingScheme": null
                        },
                        "portfolioBiddingId": null,
                        "portfolioBiddingName": null
                    },
                    "frequentlyRunBetterPerformingAdsMode": "APPLY",
                    "adGroupId": 333333,
                    "adGroupName": "auto_adgroup_01",
                    "adGroupTrackId": 0,
                    "campaignId": 222222,
                    "campaignName": "auto_campaign_01",
                    "campaignTrackId": 1234567890,
                    "customParameters": null,
                    "labels": null,
                    "settings": {
                        "criterionType": "TARGET_LIST",
                        "targetingSetting": {
                            "targetAll": "ACTIVE"
                        }
                    },
                    "trackingUrl": null,
                    "isRemoveTrackingUrl": null,
                    "urlReviewData": {
                        "disapprovalReasonCodes": null,
                        "disapprovalReviewUrl": null,
                        "inReviewUrl": null,
                        "urlApprovalStatus": "NONE"
                    },
                    "userStatus": "ACTIVE",
                    "createdDate": "20230329"
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
* 広告タイプ（ad.adType）：動的検索連動型広告（DYNAMIC_SEARCH_LINKED_AD）
* 説明文（ad.dynamicSearchLinkedAd.description）：自由記述

##### ＜リクエストサンプル＞
```json
{
  "accountId": 111111,
  "operand": [
    {
      "ad": {
        "adType": "DYNAMIC_SEARCH_LINKED_AD",
        "devicePreference": "SMART_PHONE",
        "dynamicSearchLinkedAd": {
          "description": "広告の説明文01"
        }
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
    "rid": "1234567890123456ascdefghijklmns",
    "rval": {
        "values": [
            {
                "adGroupAd": {
                    "accountId": 111111,
                    "ad": {
                        "adType": "DYNAMIC_SEARCH_LINKED_AD",
                        "textAd2": null,
                        "appAd": null,
                        "extendedTextAd": null,
                        "dynamicSearchLinkedAd": {
                            "description": "広告の説明文01",
                            "description2": null
                        },
                        "responsiveSearchAd": null,
                        "finalUrl": null,
                        "reviewFinalUrl": null,
                        "smartphoneFinalUrl": null,
                        "reviewSmartphoneFinalUrl": null,
                        "isRemoveSmartphoneFinalUrl": null,
                        "trackingUrl": null,
                        "reviewTrackingUrl": null,
                        "isRemoveTrackingUrl": null,
                        "customParameters": null,
                        "reviewCustomParameters": null,
                        "devicePreference": null,
                        "displayUrl": null,
                        "url": null
                    },
                    "adGroupId": 333333,
                    "adGroupName": "auto_adgroup_01",
                    "adGroupTrackId": 0,
                    "adId": 4444444444,
                    "adName": "広告名01",
                    "adTrackId": 0,
                    "approvalStatus": "REVIEW",
                    "campaignId": 222222,
                    "campaignName": "auto_campaign_01",
                    "campaignTrackId": 1234567890,
                    "disapprovalReasonCodes": null,
                    "feedId": null,
                    "invalidedTrademarks": null,
                    "labels": null,
                    "trademarkStatus": "NO_RESTRICTION",
                    "userStatus": "ACTIVE",
                    "createdDate": "20230329"
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}

```
