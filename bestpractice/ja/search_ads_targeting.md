# 検索広告のターゲティング
## ターゲティングとは
<a href="https://ads-help.yahoo-net.jp/s/article/H000044394?language=ja">ターゲティング</a>とは、適切なユーザーに適切なタイミングで広告を表示できる機能です。<br>
検索広告においては下記のターゲティングを利用できます。<br>
* “LOCATION” （地域ターゲティング）
* “SCHEDULE”（曜日・時間帯ターゲティング）
* “PLATFORM” (デバイスターゲティング)

## 検索広告 APIでの実施方法
検索広告APIではターゲティングを利用するために以下の3つのServiceを使用します。

##### 1. CampaignService
CampaignServiceでは、キャンペーンに関する情報の取得および追加・更新が実施できます。

##### 2. DictionaryService（地域ターゲティングを指定したい場合のみ）
DictionaryServiceでは、地域情報の一覧取得を実施できます。

##### 3. CampaignTargetService
CampaignTargetServiceでは、キャンペーンのターゲティング設定に関する情報の取得および更新を行います。

## シナリオ
検索広告APIを使いキャンペーン作成からターゲティング設定までのフローをご紹介します。<br>
本シナリオで設定するターゲティングは下記の通りとします。<br>
なお、入札価格調整率は％表記ではなく0.10～10.00の値を用います。（100%が1となります）<br>
たとえば、+30%の場合は1.3、-90%の場合は0.1のようになります。

<table class="standard">
  <tr>
　　<th>種別</th>
　　<th>ターゲティング設定</th>
　　<th>入札価格調整率</th>
　</tr>
　<tr>
　　<td>曜日・時間帯ターゲティング</td>
　　<td>土曜日の19時から24時まで</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>曜日・時間帯ターゲティング</td>
　　<td>日曜日の19時から24時まで</td>
　　<td>1.3</td>
　</tr>
　<tr>
　　<td>地域ターゲティング</td>
　　<td>東京都　配信</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>地域ターゲティング</td>
　　<td>神奈川県　横浜市　配信</td>
　　<td>0.9</td>
　</tr>
　<tr>
　　<td>地域ターゲティング</td>
　　<td>東京都　千代田区　除外</td>
　　<td></td>
　</tr>
　<tr>
　　<td>デバイスターゲティング</td>
　　<td>スマートフォン</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>デバイスターゲティング</td>
　　<td>タブレット</td>
　　<td>0.8</td>
　</tr>
</table>
<br>

#### 1. キャンペーン作成
CampaignService:addを使用し、キャンペーンを作成します。

##### ＜リクエストサンプル＞
```json
{
  "accountId": 11111111,
  "operand":[{
    "campaignName": "キャンペーンターゲットテスト",
    "userStatus": "ACTIVE",
    "budget": {
      "amount": 100
    },
    "biddingStrategyConfiguration": {
      "biddingScheme": {
        "biddingStrategyType": "CPC"
      }
    }
  }]
}
```

##### ＜レスポンスサンプル＞
※長くなるため、一部、省略しています。
```json
{
  "errors": null,
  "rid": "1",
  "rval": {
    "values": [
      {
        "campaign": {
          "accountId": 11111111,
          "appId": null,
          "appOsType": null,
          "biddingStrategyConfiguration": {
            "biddingScheme": {
              "biddingStrategyType": "CPC",
              "cpcBiddingScheme": {
                "enhancedCpcEnabled": "FALSE"
              },
              ...
            },
            "portfolioBiddingId": null,
            "portfolioBiddingName": null,
            "biddingStrategySource": "CAMPAIGN"
          },
          "biddingStrategyFailedReason": null,
          "budget": {
            "amount": 100
          },
          "campaignId": 2222222,
          "campaignName": "キャンペーンターゲットテスト",
          "campaignTrackId": 0,
          "conversionOptimizerEligibility": "DISABLE",
          "customParameters": null,
          "endDate": "20371231",
          "failedBiddingStrategyConfiguration": null,
          "labels": null,
          "servingStatus": "SERVING",
          "settings": [
            ...
          ],
          "startDate": "20231020",
          "trackingUrl": null,
          "type": "STANDARD",
          "urlReviewData": {
            ...
          },
          "userStatus": "ACTIVE",
          "createdDate": "20231020"
        },
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}
```

#### 2.	地域情報の一覧を取得
DictionaryService:getGeographicLocationを使用し、地域情報の一覧を取得します。<br>
ここで取得した一覧にあるコードは、後の手順で実施する地域ターゲティングの指定時に使います。


##### ＜リクエストサンプル＞
```json
{
  "lang": "JA"
}
```

##### ＜レスポンスサンプル＞
※長くなるため、一部、省略しています。
```json
{
  "errors": null,
  "rid": "2",
  "rval": {
    "totalNumEntries": 47,
    "values": [
      {
        "errors": null,
        "geographicLocation": {
          "child": [
            {
              "child": null,
              "code": "JP-01-0003",
              "fullName": "北海道 旭川市",
              "geographicLocationStatus": "ACTIVE",
              "name": "旭川市",
              "order": "0000000100",
              "parent": "JP-01"
            },
            ...
        {
          "errors": null,
          "geographicLocation": {
            "child": [
              {
                "child": null,
                "code": "JP-13-0002",
                "fullName": "東京都 昭島市",
                "geographicLocationStatus": "ACTIVE",
                "name": "昭島市",
                "order": "1200000100",
                "parent": "JP-13"
              },
              ...
              {
                "child": null,
                "code": "JP-13-0005",
                "fullName": "東京都 千代田区",
                "geographicLocationStatus": "ACTIVE",
                "name": "千代田区",
                "order": "1200003300",
                "parent": "JP-13"
              },
              ...
              {
                "child": null,
                "code": "JP-13-0025",
                "fullName": "東京都 目黒区",
                "geographicLocationStatus": "ACTIVE",
                "name": "目黒区",
                "order": "1200005300",
                "parent": "JP-13"
              }
            ],
            "code": "JP-13",
            "fullName": "東京都",
            "geographicLocationStatus": "ACTIVE",
            "name": "東京都",
            "order": "1200000000",
            "parent": null
          },
          "operationSucceeded": true
        },
        ...
            {
              "child": null,
              "code": "JP-14-0025",
              "fullName": "神奈川県 横浜市",
              "geographicLocationStatus": "ACTIVE",
              "name": "横浜市",
              "order": "1300002900",
              "parent": "JP-14"
            }
          ...
          ],
          "code": "JP-47",
          "fullName": "沖縄県",
          "geographicLocationStatus": "ACTIVE",
          "name": "沖縄県",
          "order": "4600000000",
          "parent": null
        },
        "operationSucceeded": true
      }
    ]
  }
}
```

#### 3.	ターゲティング設定の確認
CampaignTargetService:getを使用して、現段階のターゲティング設定を確認します。<br>
手順1を実行した段階で全てのデバイスがターゲティング対象になっていることが確認できます。

##### ＜リクエストサンプル＞
```json
{
  "accountId": 11111111,
  "campaignIds": [2222222]
}
```

##### ＜レスポンスサンプル＞

```json
{
  "errors": null,
  "rid": "3",
  "rval": {
    "totalNumEntries": 3,
    "values": [
      {
        "campaignTarget": {
          "accountId": 11111111,
          "bidMultiplier": 1.0,
          "campaignId": 2222222,
          "campaignName": "キャンペーンターゲットテスト",
          "target": {
            "locationTarget": null,
            "networkTarget": null,
            "platformTarget": {
              "platformType": "DESKTOP"
            },
            "scheduleTarget": null,
            "targetId": "4000000000",
            "targetType": "PLATFORM"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "campaignTarget": {
          "accountId": 11111111,
          "bidMultiplier": 1.0,
          "campaignId": 2222222,
          "campaignName": "キャンペーンターゲットテスト",
          "target": {
            "locationTarget": null,
            "networkTarget": null,
            "platformTarget": {
              "platformType": "SMART_PHONE"
            },
            "scheduleTarget": null,
            "targetId": "4000000001",
            "targetType": "PLATFORM"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "campaignTarget": {
          "accountId": 11111111,
          "bidMultiplier": 1.0,
          "campaignId": 2222222,
          "campaignName": "キャンペーンターゲットテスト",
          "target": {
            "locationTarget": null,
            "networkTarget": null,
            "platformTarget": {
              "platformType": "TABLET"
            },
            "scheduleTarget": null,
            "targetId": "4000000002",
            "targetType": "PLATFORM"
          }
        },
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}
```

#### 4.	ターゲティング設定の更新
CampaignTargetService:setを使用してターゲティングを更新します。<br>
ここではデバイスターゲティングを更新します。手順3で確認した通り、キャンペーン作成時点でデバイスターゲティングが設定されるので調整が必要となるためです。<br>
シナリオに合わせてPCとタブレットについて入札価格調整率を調整します。（※入札価格調整率を0にすると広告が配信されません）

##### ＜リクエストサンプル＞
```json
{
  "accountId": 11111111,
  "operand": [{
    "accountId": 11111111,
    "campaignId": 2222222,
    "bidMultiplier": 0,
    "target": {
      "platformTarget": {
        "platformType": "DESKTOP"
      },
      "targetType": "PLATFORM"
    }
  },
    {
      "accountId": 11111111,
      "campaignId": 2222222,
      "bidMultiplier": 0.8,
      "target": {
        "platformTarget": {
          "platformType": "TABLET"
        },
        "targetType": "PLATFORM"
      }
    }]
}
```

##### ＜レスポンスサンプル＞

```json
{
  "errors": null,
  "rid": "4",
  "rval": {
    "values": [
      {
        "campaignTarget": {
          "accountId": 11111111,
          "bidMultiplier": 0.0,
          "campaignId": 2222222,
          "campaignName": "キャンペーンターゲットテスト",
          "target": {
            "locationTarget": null,
            "networkTarget": null,
            "platformTarget": {
              "platformType": "DESKTOP"
            },
            "scheduleTarget": null,
            "targetId": "4000000000",
            "targetType": "PLATFORM"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "campaignTarget": {
          "accountId": 11111111,
          "bidMultiplier": 0.8,
          "campaignId": 2222222,
          "campaignName": "キャンペーンターゲットテスト",
          "target": {
            "locationTarget": null,
            "networkTarget": null,
            "platformTarget": {
              "platformType": "TABLET"
            },
            "scheduleTarget": null,
            "targetId": "4000000002",
            "targetType": "PLATFORM"
          }
        },
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}
```

#### 5.	ターゲティング設定
CampaignTargetService:addを使用して、本シナリオで必要となる曜日・時間帯ターゲティング、地域ターゲティングを設定します。

##### ＜リクエストサンプル＞
```json
{
  "accountId": 11111111,
  "operand": [{
    "accountId": 11111111,
    "campaignId": 2222222,
    "bidMultiplier": 1,
    "target": {
      "scheduleTarget": {
        "dayOfWeek": "SATURDAY",
        "startHour": 19,
        "startMinute": "ZERO",
        "endHour": 24,
        "endMinute": "ZERO"
      },
      "targetType": "SCHEDULE"
    }
  },
    {
      "accountId": 11111111,
      "campaignId": 2222222,
      "bidMultiplier": 1.3,
      "target": {
        "scheduleTarget": {
          "dayOfWeek": "SUNDAY",
          "startHour": 19,
          "startMinute": "ZERO",
          "endHour": 24,
          "endMinute": "ZERO"
        },
        "targetType": "SCHEDULE"
      }
    },
    {
      "accountId": 11111111,
      "campaignId": 2222222,
      "bidMultiplier": 1,
      "target": {
        "locationTarget": {
          "excludedType": "INCLUDED"
        },
        "targetId": "JP-13",
        "targetType": "LOCATION"
      }
    },
    {
      "accountId": 11111111,
      "campaignId": 2222222,
      "bidMultiplier": 0.9,
      "target": {
        "locationTarget": {
          "excludedType": "INCLUDED"
        },
        "targetId": "JP-14-0025",
        "targetType": "LOCATION"
      }
    },
    {
      "accountId": 11111111,
      "campaignId": 2222222,
      "target": {
        "locationTarget": {
          "excludedType": "EXCLUDED"
        },
        "targetId": "JP-13-0005",
        "targetType": "LOCATION"
      }
    }]
}
```

##### ＜レスポンスサンプル＞

```json
{
  "errors": null,
  "rid": "5",
  "rval": {
    "values": [
      {
        "campaignTarget": {
          "accountId": 11111111,
          "bidMultiplier": 1.0,
          "campaignId": 2222222,
          "campaignName": "キャンペーンターゲットテスト",
          "target": {
            "locationTarget": null,
            "networkTarget": null,
            "platformTarget": null,
            "scheduleTarget": {
              "dayOfWeek": "SATURDAY",
              "endHour": 24,
              "endMinute": "ZERO",
              "startHour": 19,
              "startMinute": "ZERO"
            },
            "targetId": "3619002400",
            "targetType": "SCHEDULE"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "campaignTarget": {
          "accountId": 11111111,
          "bidMultiplier": 1.3,
          "campaignId": 2222222,
          "campaignName": "キャンペーンターゲットテスト",
          "target": {
            "locationTarget": null,
            "networkTarget": null,
            "platformTarget": null,
            "scheduleTarget": {
              "dayOfWeek": "SUNDAY",
              "endHour": 24,
              "endMinute": "ZERO",
              "startHour": 19,
              "startMinute": "ZERO"
            },
            "targetId": "3719002400",
            "targetType": "SCHEDULE"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "campaignTarget": {
          "accountId": 11111111,
          "bidMultiplier": 1.0,
          "campaignId": 2222222,
          "campaignName": "キャンペーンターゲットテスト",
          "target": {
            "locationTarget": {
              "cityNameEN": null,
              "cityNameJA": null,
              "excludedType": "INCLUDED",
              "provinceNameEN": "Tokyo",
              "provinceNameJA": "東京都",
              "targetingStatus": "ACTIVE"
            },
            "networkTarget": null,
            "platformTarget": null,
            "scheduleTarget": null,
            "targetId": "JP-13",
            "targetType": "LOCATION"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "campaignTarget": {
          "accountId": 11111111,
          "bidMultiplier": 0.9,
          "campaignId": 2222222,
          "campaignName": "キャンペーンターゲットテスト",
          "target": {
            "locationTarget": {
              "cityNameEN": "Yokohama",
              "cityNameJA": "横浜市",
              "excludedType": "INCLUDED",
              "provinceNameEN": "Kanagawa",
              "provinceNameJA": "神奈川県",
              "targetingStatus": "ACTIVE"
            },
            "networkTarget": null,
            "platformTarget": null,
            "scheduleTarget": null,
            "targetId": "JP-14-0025",
            "targetType": "LOCATION"
          }
        },
        "errors": null,
        "operationSucceeded": true
      },
      {
        "campaignTarget": {
          "accountId": 11111111,
          "bidMultiplier": null,
          "campaignId": 2222222,
          "campaignName": "キャンペーンターゲットテスト",
          "target": {
            "locationTarget": {
              "cityNameEN": "Chiyoda",
              "cityNameJA": "千代田区",
              "excludedType": "EXCLUDED",
              "provinceNameEN": "Tokyo",
              "provinceNameJA": "東京都",
              "targetingStatus": "ACTIVE"
            },
            "networkTarget": null,
            "platformTarget": null,
            "scheduleTarget": null,
            "targetId": "JP-13-0005",
            "targetType": "LOCATION"
          }
        },
        "errors": null,
        "operationSucceeded": true
      }
    ]
  }
}
```
