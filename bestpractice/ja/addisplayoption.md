# 広告表示オプション
## 広告表示オプションとは
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
##### 1. FeedItemService
FeedItemServiceでは、FeedItem情報の取得および追加・更新・削除が実施できます。
FeedItem情報とは、広告表示オプションとして表示する、テキスト、リンクURL 、電話番号、などのコンポーネントのことです。

##### 2. CampaignFeedService
CampaignFeedServiceでは、追加したFeedItem情報のキャンペーンへの設定やキャンペーンに設定されているFeedItem情報の取得を実施できます。

##### 3. AdGroupFeedService
AdGroupFeedServiceでは、追加したFeedItem情報の広告グループへの設定や広告グループに設定されているFeedItem情報の取得を実施できます。

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

#### 1.	FeedItemの登録
はじめに、FeedItemService:addを使い、検索広告のアカウントにFeedItem情報を登録します。
ここでは、A社の検索広告のアカウント（ID:11111111）に、先述の広告表示オプションをそれぞれ登録します。
##### ＜リクエストサンプル＞ [QUICKLINK用]
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "feedItemAttribute": [
      	{
      	  "placeholderField": "LINK_TEXT",	
          "simpleFeedItemAttribute": {
            "feedAttributeValue": "セール"
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
            "feedAttributeValue": "店舗一覧"
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
            "feedAttributeValue": "ランキング"
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
            "feedAttributeValue": "問合せ"
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
            "feedAttributeValue": "クーポン"
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
            "feedAttributeValue": "特別セール"
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
            "feedAttributeValue": "ポイント"
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
##### ＜レスポンスサンプル＞ [QUICKLINK用]
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
                                "reviewFeedAttributeValue": "セール"
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
                                "reviewFeedAttributeValue": "店舗一覧"
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
                                "reviewFeedAttributeValue": "ランキング"
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
                                "reviewFeedAttributeValue": "問合せ"
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
                                "reviewFeedAttributeValue": "クーポン"
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
                                "reviewFeedAttributeValue": "特別セール"
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
                                "reviewFeedAttributeValue": "ポイント"
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
##### ＜リクエストサンプル＞ [CALLEXTENSION用]
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
##### ＜レスポンスサンプル＞ [CALLEXTENSION用]
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

##### ※FeedItemの更新について
更新時にfeedItemAttributeを指定するとすべて上書きされ、未指定のフィードアイテムの属性情報は削除されます。
また、下記の場合のみfeedAttributeValueに空文字を指定することで削除が可能です。

placeholderType   | placeholderField
----------------- | --------------------
QUICKLINK         | ADVANCED_MOBILE_URL
QUICKLINK         | TRACKING_URL
AD_CUTOMIZER      | any



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
      "campaignName": "テスト",
      "userStatus": "ACTIVE"
    }
  ]
}
```
##### ＜レスポンスサンプル＞
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
                    "campaignName": "テスト",
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
#### 2.	キャンペーンへの登録
次に、CampaignFeedService:setを使い、登録したFeedItem情報をキャンペーンに設定します。
ここではQuickLink[No1-4]とCallExtension[No1]をキャンペーンに設定します。
##### ＜リクエストサンプル＞ [QUICKLINK用]
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
##### ＜レスポンスサンプル＞ [QUICKLINK用]
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
##### ＜リクエストサンプル＞ [CALLEXTENSION用]
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
##### ＜レスポンスサンプル＞ [CALLEXTENSION用]
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
#### 2.5. アドグループの作成
登録したFeedItem情報を広告グループに設定する前に、AdGroupService:addで、アドグループを作成しておきます。
##### ＜リクエストサンプル＞
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "adGroupName": "アドグループテスト",
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
                    "adGroupName": "アドグループテスト",
                    ...
                    "campaignId": 22222222,
                    "campaignName": "テスト",
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

#### 3.	広告グループへの登録
続いてAdGroupFeedService:setを使い、登録したFeedItem情報を広告グループに設定します。
ここではQuickLink[No5]を広告グループに設定します。
##### ＜リクエストサンプル＞ [QUICKLINK用]
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
##### ＜レスポンスサンプル＞ [QUICKLINK用]
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
##### ＜リクエストサンプル＞ [CALLEXTENSION用]
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
##### ＜レスポンスサンプル＞ [CALLEXTENSION用]
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
#### 4.	キャンペーンのFeedItem変更
特別セールの開催が決まったため、CampaignFeedService:setで、キャンペーンに設定しているQuickLinkを変更します。
今回は、キャンペーンに設定しているQuickLink[No1]を削除し、新たにQuickLink[No6]を設定します。
##### ＜リクエストサンプル＞ [QUICKLINK用]
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
##### ＜レスポンスサンプル＞ [QUICKLINK用]
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
##### ＜リクエストサンプル＞ [CALLEXTENSION用]
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
##### ＜レスポンスサンプル＞ [CALLEXTENSION用]
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
#### 5.	広告グループのFeedItem変更
クーポンの提供期間が終了したため、AdGroupFeedService:setで、ポイントキャンペーンへの誘導ページに変更します。
今回は、広告グループに設定しているQuickLink[No5]を削除し、新たにQuickLink[No7]を設定します。
##### ＜リクエストサンプル＞
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
##### ＜レスポンスサンプル＞
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

#### 6.	CallExtensionの解除
電話窓口が廃止になったため、AdGroupFeed:setで、広告グループに設定されているCallExtensionを解除します。
##### ＜リクエストサンプル＞
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
##### ＜レスポンスサンプル＞
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
