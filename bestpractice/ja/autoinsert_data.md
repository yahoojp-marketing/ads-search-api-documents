# アドカスタマイザー機能（データの自動挿入）
## アドカスタマイザーとは
アドカスタマイザーとは、検索広告の広告文面を動的に変更できる機能です。<br>
広告のタイトルや説明文に任意のテキストを自動挿入できます。また、カウントダウン関数を使って、セール終了までの時間をカウントダウン表示できます。<br>
アドカスタマイザーについて、詳しくは以下のヘルプをご参照ください。<br>
・<a href="https://ads-help.yahoo-net.jp/s/article/H000044652?language=ja">アドカスタマイザーについて</a><br>

## 検索広告API での実施方法
検索広告APIではアドカスタマイザーを利用するために、以下の3つのServiceを使用します。
##### 1. FeedService
FeedServiceでは、Feed情報の追加・更新・削除ができます。<br>
Feed情報とは、広告に挿入するデータを登録したデータ自動挿入リストを格納するコンポーネントです。

##### 2. FeedItemService
FeedItemServiceでは、Feed情報内の各データ自動挿入リストに、データを追加・更新・削除できます。

##### 3. AdGroupAdService
AdGroupAdServiceでは、登録したデータを挿入する広告（データ挿入用の関数を使用した広告）を作成できます。

## シナリオ
A社は、販促施策の一環として、検索広告APIを使い、以下のデータセットを作成します。

##### セール商品リスト
<table class="standard">
                <tr>
                    <th valign="top" >
                        <p>商品 (String)</p>
                    </th>
                    <th valign="top" >
                        <p>価格 (Price)</p>
                    </th>
                    <th valign="top">
                        <p>セール終了日 (Date)</p>
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
                        <p>製品101</p>
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
                        <p>製品102</p>
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
                        <p>製品103</p>
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
※CampaignIdやAdGroupIdIDを設定することで、そのデータ行の利用対象とするキャンペーンや広告グループを指定できます。<br>

#### 1.	Feedの登録
はじめに、FeedService:addを使い、検索広告のアカウントにFeed情報を登録します。<br>
ここでは、A社の検索広告のアカウント（ID:111111）に、「セール商品リスト」という名前で登録します。

##### リクエストサンプル
```json
{
  "accountId": 111111,
  "operand": [
    {
      "feedAttribute": [
        {
          "feedAttributeName": "商品名",
          "placeholderField": "AD_CUSTOMIZER_STRING"
        },
        {
          "feedAttributeName": "価格",
          "placeholderField": "AD_CUSTOMIZER_PRICE"
        },
        {
          "feedAttributeName": "セール終了日",
          "placeholderField": "AD_CUSTOMIZER_DATE"
        }
      ],
      "feedName": "セール商品リスト",
      "placeholderType": "AD_CUSTOMIZER"
    }
  ]
}
```

##### レスポンスサンプル
```json
{
    "errors": null,
    "rid": "1daee6f901327fad5d203ce65b941c17",
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
                            "feedAttributeName": "商品名",
                            "placeholderField": "AD_CUSTOMIZER_STRING"
                        },
                        {
                            "feedAttributeId": 2,
                            "feedAttributeName": "価格",
                            "placeholderField": "AD_CUSTOMIZER_PRICE"
                        },
                        {
                            "feedAttributeId": 3,
                            "feedAttributeName": "セール終了日",
                            "placeholderField": "AD_CUSTOMIZER_DATE"
                        }
                    ],
                    "feedId": 222222,
                    "feedName": "セール商品リスト",
                    "feedTrackId": 0,
                    "placeholderType": "AD_CUSTOMIZER"
                },
                "operationSucceeded": true
            }
        ]
    }
}
```
#### 1.1. キャンペーンの作成
FeedItemを登録する前に、CampaignService:addで、キャンペーンを2つ作っておきます。
##### ＜リクエストサンプル＞ ad_campaign_1
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
##### ＜レスポンスサンプル＞ ad_campaign_1
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
##### ＜リクエストサンプル＞ ad_campaign_2
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
##### ＜レスポンスサンプル＞ ad_campaign_2
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
#### 1.2. 広告グループの作成
登録したFeedItem情報を広告グループに設定する前に、AdGroupService:addで、広告グループを作成しておきます。<br>
##### ＜リクエストサンプル＞ ad_adgroup_1
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
##### ＜レスポンスサンプル＞ ad_adgroup_1
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
##### ＜リクエストサンプル＞ ad_adgroup_2
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
##### ＜レスポンスサンプル＞ ad_adgroup_2
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
#### 1.3. キーワードの作成
FeedItemを登録する前に、AdGroupCriterionService:addで、キーワードを2つ作っておきます。

##### ＜リクエストサンプル＞
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
##### ＜レスポンスサンプル＞
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

#### 2. FeedItemの登録
次にFeedItemService:addを使い、登録したFeed情報に、広告に挿入・設定するデータを設定します。

##### リクエストサンプル
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
            "feedAttributeValue": "製品101"
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
            "feedAttributeValue": "製品102"
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
            "feedAttributeValue": "製品103"
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

##### レスポンスサンプル
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
                                "reviewFeedAttributeValue": "製品101"
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
                                "reviewFeedAttributeValue": "製品102"
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
                                "reviewFeedAttributeValue": "製品103"
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

#### 3.	AdGroupAdの登録
続いて登録したデータを挿入する広告を、AdGroupAdService:addを使用して登録します。<br>
アドカスタマイザーでデータを自動挿入した広告を配信するには、通常の広告も有効にしておく必要があるため、この例では同時に登録を行っています。<br>

<b>■ヒント</b><br>
カウントダウン関数を使用すると、広告内にセールやキャンペーンなどの終了までの残り時間を表示できます。また、カウントダウンの終了とともに、広告配信を停止できます。詳しくは以下のヘルプをご参照ください。<br>
・<a href="https://ads-help.yahoo-net.jp/s/article/H000044692?language=ja">カウントダウン関数について</a>

##### リクエストサンプル
```json
{
  "accountId": 111111,
  "operand": [
    {
      "ad": {
        "adType": "EXTENDED_TEXT_AD",
        "advancedUrl": "http://www.example.jp",
        "description": "{=セール商品リスト.価格}円で販売。",
        "extendedTextAd": {
          "headline2": "終了まであと{=COUNTDOWN(セール商品リスト.セール終了日,\"ja\")}"
        },
        "headline": "人気の{=セール商品リスト.商品名}が大特価"
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
        "description": "期間限定特別価格で販売。",
        "extendedTextAd": {
          "headline2": "１２月３１日まで"
        },
        "headline": "人気の商品が大特価"
      },
      "adGroupId": 600002,
      "adName": "Best Practice Simple Ads",
      "campaignId": 500002,
      "userStatus": "ACTIVE"
    }
  ]
}
```

##### レスポンスサンプル
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
                        "description": "{=セール商品リスト.価格}円で販売。",
                        "devicePreference": null,
                        "displayUrl": "www.example.jp",
                        "extendedTextAd": {
                            "headline2": "終了まであと{=COUNTDOWN(セール商品リスト.セール終了日,\"ja\")}",
                            ...
                        },
                        "headline": "人気の{=セール商品リスト.商品名}が大特価",
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
                        "description": "期間限定特別価格で販売。",
                        "devicePreference": null,
                        "displayUrl": "www.example.jp",
                        "extendedTextAd": {
                            "headline2": "１２月３１日まで",
                            ...
                        },
                        "headline": "人気の商品が大特価",
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

#### 4.	キャンペーンのFeedItem変更
広告入稿後に価格の変動があったため、以下のデータに変更する必要があります。<br>
アドカスタマイザーではFeedItemService:setを使用し、データを更新するだけで広告文面を自動で変更できます。

##### セール商品リスト（変更後）
<table class="standard">
                <tr>
                    <th valign="top" >
                        <p>商品 (String)</p>
                    </th>
                    <th valign="top" >
                        <p>価格 (Price)</p>
                    </th>
                    <th valign="top">
                        <p>セール終了日 (Date)</p>
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
                        <p>製品101</p>
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
                        <p>製品102</p>
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
                        <p>製品103</p>
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

##### リクエストサンプル
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

##### レスポンスサンプル
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
                                "reviewFeedAttributeValue": "製品101"
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
                                "feedAttributeValue": "製品102",
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
                                "feedAttributeValue": "製品103",
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
