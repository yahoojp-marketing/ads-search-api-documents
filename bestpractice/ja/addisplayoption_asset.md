# 広告表示オプション
## 広告表示オプションとは
※こちらの利用方法は、2022年春にリリース予定の新形式の方法となります。

<a href="https://ads-help.yahoo.co.jp/yahooads/ss/articledetail?lan=ja&aid=1033">広告表示オプション</a>とは、検索広告に、別ページへのリンク、電話番号、といった付加情報をつけて配信する機能です。

広告表示オプションには、以下の4つがあります：
* “QuickLink” （広告の下部に別ページへのリンクを表示）
* “CallExtension”（電話番号を表示）
* “CALLOUT” (テキスト補足オプション)
* “STRUCTURED_SNIPPET” (カテゴリ補足オプション)

広告表示オプションには、以下のメリットがあります。
1. 広告スペースが広がるため、視認性が高まる。 → クリック率向上
2. ユーザーが求めているページに、すぐにアクセスできる。 → 利便性の向上

## 検索広告 APIでの実施方法
検索広告APIでは、広告表示オプションを表示するために、以下の3つのServiceを使用します。
##### 1. AssetService
AssetServiceでは、Asset情報の取得および追加・更新が実施できます。
Asset情報とは、広告表示オプションとして表示する、テキスト、リンクURL 、電話番号、などのコンポーネントのことです。

##### 2. CampaignAssetService
CampaignAssetServiceでは、追加したAsset情報のキャンペーンへの設定やキャンペーンに設定されているAsset情報の取得を実施できます。

##### 3. AdGroupAssetService
AdGroupAssetServiceでは、追加したAsset情報の広告グループへの設定や広告グループに設定されているAsset情報の取得を実施できます。

## シナリオ
A社は、販促施策の一環として、検索広告APIを使い、以下の広告表示オプションの追加を行います。

##### QuickLink
No                | LINK_TEXT             | LINK_URL
----------------- | --------------------- | -----------------------------------------
1 | セール | www.example.jp/sale
2 | 店舗一覧 | www.example.jp/store
3 | ランキング | www.example.jp/ranking
4 | 問い合わせ | www.example.jp/support
5 | クーポン | www.example.jp/coupon
6 | 特別セール | www.example.jp/specialsale
7 | ポイント | www.example.jp/point

##### CallExtension
No                | CALL_PHONE_NUMBER
----------------- | ---------------------
1 | 0120-45-6789

#### 1. Asset情報の登録
はじめに、AssetService:addを使い、検索広告のアカウントにAsset情報を登録します。
ここでは、A社の検索広告のアカウント（ID:11111111）に、先述の広告表示オプションをそれぞれ登録します。
##### ＜リクエストサンプル＞ [QUICKLINK用]
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "assetData": {
        "type": "QUICKLINK",
        "quickLinkAsset": {
          "linkText": "セール"
        }
      },
      "finalUrl": "http://www.example.jp/sale"
    },
    {
      "assetData": {
        "type": "QUICKLINK",
        "quickLinkAsset": {
          "linkText": "店舗一覧"
        }
      },
      "finalUrl": "http://www.example.jp/store"
    },
    {
      "assetData": {
        "type": "QUICKLINK",
        "quickLinkAsset": {
          "linkText": "ランキング"
        }
      },
      "finalUrl": "http://www.example.jp/ranking"
    },
    {
      "assetData": {
        "type": "QUICKLINK",
        "quickLinkAsset": {
          "linkText": "問い合わせ"
        }
      },
      "finalUrl": "http://www.example.jp/support"
    },
    {
      "assetData": {
        "type": "QUICKLINK",
        "quickLinkAsset": {
          "linkText": "クーポン"
        }
      },
      "finalUrl": "http://www.example.jp/coupon"
    },
    {
      "assetData": {
        "type": "QUICKLINK",
        "quickLinkAsset": {
          "linkText": "特別セール"
        }
      },
      "finalUrl": "http://www.example.jp/specialsale"
    },
    {
      "assetData": {
        "type": "QUICKLINK",
        "quickLinkAsset": {
          "linkText": "ポイント"
        }
      },
      "finalUrl": "http://www.example.jp/point"
    }
  ]
}
```
##### ＜レスポンスサンプル＞ [QUICKLINK用]
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
              "linkText": "セール",
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
   ~~~~~~~~省略~~~~~~~~
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
##### ＜リクエストサンプル＞ [CALLEXTENSION用]
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
##### ＜レスポンスサンプル＞ [CALLEXTENSION用]
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

#### 1.5. キャンペーンの作成
キャンペーンを登録する前に、CampaignService:addで、キャンペーンを作っておきます。
##### ＜リクエストサンプル＞
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
      "campaignName": "キャンペーンテスト",
      "userStatus": "ACTIVE"
    }
  ]
}
```
##### ＜レスポンスサンプル＞
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
          "campaignName": "テストテストテスト1",
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
#### 2. キャンペーンへの登録
次に、CampaignAssetService:replaceを使い、登録したAsset情報をキャンペーンに設定します。
ここではQuickLink[No1-4]とCallExtension[No1]をキャンペーンに設定します。
##### ＜リクエストサンプル＞ [QUICKLINK用]
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
##### ＜レスポンスサンプル＞ [QUICKLINK用]
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
##### ＜リクエストサンプル＞ [CALLEXTENSION用]
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
##### ＜レスポンスサンプル＞ [CALLEXTENSION用]
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
#### 2.5. 広告グループの作成
登録したAsset情報を広告グループに設定する前に、AdGroupService:addで、広告グループを作成しておきます。
##### ＜リクエストサンプル＞
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "adGroupName": "広告グループテスト",
      "campaignId": 22222222,
      "userStatus": "ACTIVE"
    }
  ]
}
```
##### ＜レスポンスサンプル＞
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
          "adGroupName": "広告グループテスト",
          "adGroupTrackId": 0,
          "bid": {
            "bidSource": "ADGROUP",
            "cpc": 1
          },
          "campaignId": 22222222,
          "campaignName": "キャンペーンテスト",
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

#### 3. 広告グループへの登録
続いてAdGroupAssetService:replaceを使い、登録したAsset情報を広告グループに設定します。
ここではQuickLink[No5]を広告グループに設定します。
##### ＜リクエストサンプル＞ [QUICKLINK用]
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
##### ＜レスポンスサンプル＞ [QUICKLINK用]
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
##### ＜リクエストサンプル＞ [CALLEXTENSION用]
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
##### ＜レスポンスサンプル＞ [CALLEXTENSION用]
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
#### 4. キャンペーンのAsset情報変更
特別セールの開催が決まったため、CampaignAssetService:replaceで、キャンペーンに設定しているQuickLinkを変更します。
今回は、キャンペーンに設定しているQuickLink[No1]を削除し、新たにQuickLink[No6]を設定します。
※・更新は常に上書きされるため追加分を含めて更新する必要があります。
 ・Asset情報を解除するときはcampaignAssetsを空の情報で更新します。
##### ＜リクエストサンプル＞ [QUICKLINK用]
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
##### ＜レスポンスサンプル＞ [QUICKLINK用]
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

#### 5. 広告グループのAsset情報変更
クーポンの提供期間が終了したため、AdGroupAssetService:replaceで、ポイントキャンペーンへの誘導ページに変更します。
今回は、広告グループに設定しているQuickLink[No5]を削除し、新たにQuickLink[No7]を設定します。
##### ＜リクエストサンプル＞
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
##### ＜レスポンスサンプル＞
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

#### 6. CallExtensionの解除
電話窓口が廃止になったため、AdGroupAssetService:replaceで、広告グループに設定されているCallExtensionを解除します。
##### ＜リクエストサンプル＞
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
##### ＜レスポンスサンプル＞
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

#### 7.キャンペーンとアセット間の設定ステータスを変更する
QuickLink[No2]の設定ステータスを一時停止とするため、CampaignAssetService:setで、キャンペーンとアセット間の設定ステータスを一時停止に変更します。
##### ＜リクエストサンプル＞
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
##### ＜レスポンスサンプル＞
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
