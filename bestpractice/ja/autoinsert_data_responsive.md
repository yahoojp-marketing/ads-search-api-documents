# アドカスタマイザー機能（レスポンシブ検索広告版）
## アドカスタマイザーとは
アドカスタマイザーとは、検索広告の広告文面を動的に変更できる機能です。<br>
広告のタイトルや説明文に任意のテキストを自動挿入できます。また、カウントダウン関数を使って、セール終了までの時間をカウントダウン表示できます。<br>
アドカスタマイザーについて、詳しくは以下のヘルプをご参照ください。<br>
・<a href="https://ads-help.yahoo-net.jp/s/article/H000044652?language=ja">アドカスタマイザーについて</a><br>
・<a href="https://ads-help.yahoo-net.jp/s/article/H000044220?language=ja">レスポンシブ検索広告とは</a><br>

## 検索広告API での実施方法
検索広告APIではアドカスタマイザーを利用するために、以下のServiceを使用します。

##### 1. CustomizerAttributeService
カスタマイザー属性の取得および追加・削除を行います。<br>
アカウント/キャンペーン/広告グループ/キーワードとカスタマイザー属性間の設定情報の追加をする際、先にカスタマイザー属性の追加を行ってください。

##### 2. AccountCustomizerService
アカウントとカスタマイザー属性間の設定情報の取得および追加・削除を行います。

##### 3. CampaignCustomizerService
キャンペーンとカスタマイザー属性間の設定情報の取得および追加・削除を行います。

##### 4. AdGroupCustomizerService
広告グループとカスタマイザー属性間の設定情報の取得および追加・削除を行います。

##### 5. AdGroupCriterionCustomizerService
キーワードとカスタマイザー属性間の設定情報の取得および追加・削除を行います。

##### 6. AdGroupAdService
登録したデータを挿入する広告（データ挿入用の関数を使用した広告）に関する情報の取得および追加・更新・削除を行います。

## シナリオ
A社は、販促施策の一環として、検索広告APIを使い、以下のデータセットを作成します。

##### セール商品リスト
<table class="standard">
  <tr>
    <th valign="top">アカウント名<br>（AccountId）</th>
    <th valign="top">キャンペーン名<br>（CampaignId）</th>
    <th valign="top">広告グループ<br>（AdGroupId）</th>
    <th valign="top">キーワード<br>（CriterionId）</th>
    <th valign="top">商品名<br>（TEXT）</th>
    <th valign="top">最安値<br>（PRICE）</th>
    <th valign="top">モデル数<br>（NUMBER）</th>
    <th valign="top">割引率<br>（PERCENT）</th>
  </tr>
  <tr>
    <th valign="top">てすと１50<br>（111111）</th>
    <th valign="top"></th>
    <th valign="top"></th>
    <th valign="top"></th>
    <th valign="top">最新モデル</th>
    <th valign="top">$100</th>
    <th valign="top">50</th>
    <th valign="top">10%</th>
  </tr>
  <tr>
    <th valign="top">てすと１50<br>（111111）</th>
    <th valign="top">家電セール<br>（222222）</th>
    <th valign="top"></th>
    <th valign="top"></th>
    <th valign="top">格安家電</th>
    <th valign="top">$80</th>
    <th valign="top">100</th>
    <th valign="top">10%</th>
  </tr>
  <tr>
    <th valign="top">てすと１50<br>（111111）</th>
    <th valign="top">家電セール<br>（222222）</th>
    <th valign="top">テレビ<br>（333333）</th>
    <th valign="top"></th>
    <th valign="top">人気テレビ</th>
    <th valign="top">$500</th>
    <th valign="top">30</th>
    <th valign="top">20%</th>
  </tr>
  <tr>
    <th valign="top">てすと１50<br>（111111）</th>
    <th valign="top">家電セール<br>（222222）</th>
    <th valign="top">テレビ<br>（333333）</th>
    <th valign="top">4K<br>（444444）</th>
    <th valign="top">4Kテレビ</th>
    <th valign="top">$800</th>
    <th valign="top">8</th>
    <th valign="top">30%</th>
  </tr>
</table>
※1つのアカウントに対し、属性名は40個まで登録できます。<br>
※アカウント/キャンペーン/広告グループ/キーワードで、同じ属性名で別の属性値が登録されたとき、配信時に下位エンティティの設定が優先されます。<br>

#### 1.	CustomizerAttributeService
カスタマイザー属性の情報を追加するときは、CustomizerAttributeService/addを使います。<br>

##### リクエストサンプル
```json
{
  "accountId": 111111,
  "operand": [
    {
      "name": "商品名",
      "type": "TEXT"
    },
    {
      "name": "最安値",
      "type": "PRICE"
    },
    {
      "name": "モデル数",
      "type": "NUMBER"
    },
    {
      "name": "割引率",
      "type": "PERCENT"
    }
  ]
}
```
##### レスポンスサンプル
```json
{
    "errors": null,
    "rid": "23eed375ce1c2d467d88ecaebc22b68c",
    "rval": {
        "values": [
            {
                "errors": null,
                "customizerAttribute": {
                    "accountId": 111111,
                    "customizerAttributeId": 555555,
                    "name": "商品名",
                    "type": "TEXT"
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "customizerAttribute": {
                    "accountId": 111111,
                    "customizerAttributeId": 666666,
                    "name": "最安値",
                    "type": "PRICE"
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "customizerAttribute": {
                    "accountId": 111111,
                    "customizerAttributeId": 777777,
                    "name": "モデル数",
                    "type": "NUMBER"
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "customizerAttribute": {
                    "accountId": 111111,
                    "customizerAttributeId": 888888,
                    "name": "割引率",
                    "type": "PERCENT"
                },
                "operationSucceeded": true
            }
        ]
    }
}
```
#### 2.	AccountCustomizerService
アカウントとカスタマイザー属性間の設定情報を追加するときは、AccountCustomizerService/addを使います。<br>

##### リクエストサンプル
```json
{
  "accountId": 111111,
  "operand": [
    {
      "customizerAttributeId": 555555,
      "value": "最新モデル"
    },
    {
      "customizerAttributeId": 666666,
      "value": "$100"
    },
    {
      "customizerAttributeId": 777777,
      "value": "50"
    },
    {
      "customizerAttributeId": 888888,
      "value": "10%"
    }
  ]
}
```
##### レスポンスサンプル
```json
{
    "errors": null,
    "rid": "a10c6dd1f72911dc3a1cf2c3ac525790",
    "rval": {
        "values": [
            {
                "errors": null,
                "accountCustomizer": {
                    "accountId": 111111,
                    "customizerAttributeId": 555555,
                    "value": "最新モデル",
                    "approvalStatus": "REVIEW",
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "accountCustomizer": {
                    "accountId": 111111,
                    "customizerAttributeId": 666666,
                    "value": "$100",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "accountCustomizer": {
                    "accountId": 111111,
                    "customizerAttributeId": 777777,
                    "value": "50",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "accountCustomizer": {
                    "accountId": 111111,
                    "customizerAttributeId": 888888,
                    "value": "10%",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            }
        ]
    }
}

```
#### 3.	CampaignCustomizerService
キャンペーンとカスタマイザー属性間の設定情報を追加するときは、CampaignCustomizerService/addを使います。<br>

##### リクエストサンプル
```json
{
  "accountId": 111111,
  "operand": [
    {
      "campaignId": 222222,
      "customizerAttributeId": 555555,
      "value": "格安家電"
    },
    {
      "campaignId": 222222,
      "customizerAttributeId": 666666,
      "value": "$80"
    },
    {
      "campaignId": 222222,
      "customizerAttributeId": 777777,
      "value": "100"
    },
    {
      "campaignId": 222222,
      "customizerAttributeId": 888888,
      "value": "10%"
    }
  ]
}
```
##### レスポンスサンプル
```json
{
    "errors": null,
    "rid": "ffde17246767f62feff67e26de6c8a79",
    "rval": {
        "values": [
            {
                "errors": null,
                "campaignCustomizer": {
                    "accountId": 111111,
                    "campaignId": 222222,
                    "customizerAttributeId": 555555,
                    "value": "格安家電",
                    "approvalStatus": "REVIEW",
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "campaignCustomizer": {
                    "accountId": 111111,
                    "campaignId": 222222,
                    "customizerAttributeId": 666666,
                    "value": "$80",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "campaignCustomizer": {
                    "accountId": 111111,
                    "campaignId": 222222,
                    "customizerAttributeId": 777777,
                    "value": "100",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "campaignCustomizer": {
                    "accountId": 111111,
                    "campaignId": 222222,
                    "customizerAttributeId": 888888,
                    "value": "10%",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            }
        ]
    }
}
```
#### 4.	AdGroupCustomizerService
広告グループとカスタマイザー属性間の設定情報を追加するときは、AdGroupCustomizerService/addを使います。<br>

##### リクエストサンプル
```json
{
  "accountId": 111111,
  "operand": [
    {
      "adGroupId": 333333,
      "customizerAttributeId": 555555,
      "value": "人気テレビ"
    },
    {
      "adGroupId": 333333,
      "customizerAttributeId": 666666,
      "value": "$500"
    },
    {
      "adGroupId": 333333,
      "customizerAttributeId": 777777,
      "value": "30"
    },
    {
      "adGroupId": 333333,
      "customizerAttributeId": 888888,
      "value": "20%"
    }
  ]
}
```
##### レスポンスサンプル
```json
{
    "errors": null,
    "rid": "07651bf1409e00247ad811ffd1004bb3",
    "rval": {
        "values": [
            {
                "errors": null,
                "adGroupCustomizer": {
                    "accountId": 111111,
                    "adGroupId": 333333,
                    "customizerAttributeId": 555555,
                    "value": "人気テレビ",
                    "approvalStatus": "REVIEW",
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "adGroupCustomizer": {
                    "accountId": 111111,
                    "adGroupId": 333333,
                    "customizerAttributeId": 666666,
                    "value": "$500",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "adGroupCustomizer": {
                    "accountId": 111111,
                    "adGroupId": 333333,
                    "customizerAttributeId": 777777,
                    "value": "30",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "adGroupCustomizer": {
                    "accountId": 111111,
                    "adGroupId": 333333,
                    "customizerAttributeId": 888888,
                    "value": "20%",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            }
        ]
    }
}
```
#### 5.	AdGroupCriterionCustomizerService
キーワードとカスタマイザー属性間の設定情報を追加するときは、AdGroupCriterionCustomizerService/addを使います。<br>

##### リクエストサンプル
```json
{
  "accountId": 111111,
  "operand": [
    {
      "criterionId": 444444,
      "customizerAttributeId": 555555,
      "value": "4Kテレビ"
    },
    {
      "criterionId": 444444,
      "customizerAttributeId": 666666,
      "value": "$800"
    },
    {
      "criterionId": 444444,
      "customizerAttributeId": 777777,
      "value": "8"
    },
    {
      "criterionId": 444444,
      "customizerAttributeId": 888888,
      "value": "30%"
    }
  ]
}
```
##### レスポンスサンプル
```json
{
    "errors": null,
    "rid": "080fded16a1a522fce1c4432dc3b13b7",
    "rval": {
        "values": [
            {
                "errors": null,
                "adGroupCustomizer": {
                    "accountId": 111111,
                    "criterionId": 444444,
                    "customizerAttributeId": 555555,
                    "value": "4Kテレビ",
                    "approvalStatus": "REVIEW",
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "adGroupCustomizer": {
                    "accountId": 111111,
                    "criterionId": 444444,
                    "customizerAttributeId": 666666,
                    "value": "$800",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "adGroupCustomizer": {
                    "accountId": 111111,
                    "criterionId": 444444,
                    "customizerAttributeId": 777777,
                    "value": "8",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            },
            {
                "errors": null,
                "adGroupCustomizer": {
                    "accountId": 111111,
                    "criterionId": 444444,
                    "customizerAttributeId": 888888,
                    "value": "30%",
                    "approvalStatus": null,
                    "disapprovalReasonCodes": null
                },
                "operationSucceeded": true
            }
        ]
    }
}
```
#### 6.	AdGroupAdService
登録したデータを挿入する広告（データ挿入用の関数を使用した広告）を追加するときは、AdGroupAdService/addを使います。<br>
また、カウントダウン関数を使用すると、広告内にセールやキャンペーンなどの終了までの残り時間を表示できます。そしてカウントダウンの終了とともに、そのAssetは無効になります。<br>
そのため、カウントダウン関数を使用したAssetは、Headlines（タイトル）とDescriptions（説明文）の最低数としてカウントしませんが、最大数としてはカウントする必要があります。<br>
例えば、Descriptionsは最低2件、最大4件の指定が必要ですが、カウントダウン関数を含めないDescriptionsを2件以上、カウントダウン関数の有無関係なしのDescriptionsを4件以内の登録が必要です。<br>

カウントダウン関数（レスポンシブ検索広告用）について、詳しくは以下のヘルプをご参照ください。<br>
・<a href="https://ads-help.yahoo-net.jp/s/article/H000044277?language=ja">カウントダウン関数（レスポンシブ検索広告用）</a>

##### リクエストサンプル
```json
{
  "accountId": 111111,
  "operand": [
    {
      "ad": {
        "adType": "RESPONSIVE_SEARCH_AD",
        "finalUrl": "http://www.example.jp",
        "responsiveSearchAd": {
          "headlines": [
            {
              "text": "{CUSTOMIZER.商品名:デフォルト値}がお買い得",
              "pinnedField": "HEADLINE1"
            },
            {
              "text": "納得価格の{CUSTOMIZER.最安値:デフォルト値}",
              "pinnedField": "HEADLINE2"
            },
            {
              "text": "今なら{CUSTOMIZER.割引率:デフォルト値}引き",
              "pinnedField": "HEADLINE3"
            },
            {
              "text": "あと{COUNTDOWN(2022-06-01 00:00:00,30)}で終了",
              "pinnedField": "UNSPECIFIED"
            }
          ],
          "descriptions": [
            {
              "text": "最新機種の{CUSTOMIZER.商品名:デフォルト値}が今だけ{CUSTOMIZER.最安値:デフォルト値}から！",
              "pinnedField": "DESCRIPTION1"
            },
            {
              "text": "全モデル{CUSTOMIZER.モデル数:デフォルト値}種類が{CUSTOMIZER.割引率:デフォルト値}以上オフ",
              "pinnedField": "DESCRIPTION2"
            },
            {
              "text": "あと{COUNTDOWN(2022-06-01 00:00:00,30)}で終了するのでお急ぎください。",
              "pinnedField": "UNSPECIFIED"
            }
          ]
        }
      },
      "adGroupId": 333333,
      "adName": "Auto Ads",
      "campaignId": 222222,
      "userStatus": "ACTIVE"
    }
  ]
}
```
##### レスポンスサンプル
```json
{
    "errors": null,
    "rid": "50ec2df1d0bc693de9289fef50bd9045",
    "rval": {
        "values": [
            {
                "adGroupAd": {
                    "accountId": 111111,
                    "ad": {
                        "adType": "RESPONSIVE_SEARCH_AD",
                        "smartphoneFinalUrl": null,
                        "finalUrl": "http://www.example.jp",
                        "appAd": null,
                        "customParameters": null,
                        "description1": null,
                        "devicePreference": null,
                        "displayUrl": "www.example.jp",
                        "extendedTextAd": null,
                        "responsiveSearchAd": {
                            "headlines": [
                                {
                                    "text": "{CUSTOMIZER.商品名:デフォルト値}がお買い得",
                                    "pinnedField": "HEADLINE1",
                                    "approvalStatus": "REVIEW",
                                    "disapprovalReasonCodes": null
                                },
                                {
                                    "text": "納得価格の{CUSTOMIZER.最安値:デフォルト値}",
                                    "pinnedField": "HEADLINE2",
                                    "approvalStatus": "REVIEW",
                                    "disapprovalReasonCodes": null
                                },
                                {
                                    "text": "今なら{CUSTOMIZER.割引率:デフォルト値}引き",
                                    "pinnedField": "HEADLINE3",
                                    "approvalStatus": "REVIEW",
                                    "disapprovalReasonCodes": null
                                },
                                {
                                    "text": "あと{COUNTDOWN(2022-06-01 00:00:00,30)}で終了",
                                    "pinnedField": "UNSPECIFIED",
                                    "approvalStatus": "REVIEW",
                                    "disapprovalReasonCodes": null
                                }
                            ],
                            "descriptions": [
                                {
                                    "text": "最新機種の{CUSTOMIZER.商品名:デフォルト値}が今だけ{CUSTOMIZER.最安値:デフォルト値}から！",
                                    "pinnedField": "DESCRIPTION1",
                                    "approvalStatus": "REVIEW",
                                    "disapprovalReasonCodes": null
                                },
                                {
                                    "text": "全モデル{CUSTOMIZER.モデル数:デフォルト値}種類が{CUSTOMIZER.割引率:デフォルト値}以上オフ",
                                    "pinnedField": "DESCRIPTION2",
                                    "approvalStatus": "REVIEW",
                                    "disapprovalReasonCodes": null
                                },
                                {
                                    "text": "あと{COUNTDOWN(2022-06-01 00:00:00,30)}で終了するのでお急ぎください。",
                                    "pinnedField": "UNSPECIFIED",
                                    "approvalStatus": "REVIEW",
                                    "disapprovalReasonCodes": null
                                }
                            ],
                            "path1": null,
                            "path2": null
                        },
                        "headline1": null,
                        "textAd2": null,
                        "dynamicSearchLinkedAd": null,
                        "trackingUrl": null,
                        "url": null
                    },
                    "adGroupId": 333333,
                    "adGroupName": "テレビ",
                    "adGroupTrackId": 134525846777,
                    "adId": 999999,
                    "adName": "Auto Ads",
                    "adTrackId": 0,
                    "approvalStatus": "REVIEW",
                    "campaignId": 222222,
                    "campaignName": "家電セール",
                    "campaignTrackId": 17246010137,
                    "disapprovalReasonCodes": null,
                    "feedId": null,
                    "invalidedTrademarks": null,
                    "labels": null,
                    "trademarkStatus": "NO_RESTRICTION",
                    "userStatus": "ACTIVE",
                    "createdDate": "20220513"
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
