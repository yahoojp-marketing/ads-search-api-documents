# 検索広告レポートの作成・取得
## パフォーマンスレポートとは
パフォーマンスレポートはキャンペーン、広告グループ、広告、キーワードなどのパフォーマンスを確認するための機能です。
パフォーマンスレポートは、パフォーマンスを表示する階層、表示項目、集計期間などの設定により、広告主様のニーズにあわせたカスタマイズが可能です。

広告管理ツールで提供しているレポート機能をAPIでもサポートしています。
## 検索広告 APIでの実施方法
検索広告APIではレポートを表示するために、ReportDefinitionService、というServiceを使用します。<br>
ReportDefinitionServiceでは、レポート出力項目の取得およびレポート作成・取得・ダウンロードを行います。<br>

## シナリオ
パフォーマンスレポート取得のため、検索広告APIを使い以下のレポート作成からダウンロードまでのフローをご紹介します。

#### 1. レポートのフィールド情報の取得
ReportDefinitionServiceのgetReportFieldsを使用します。
ReportTypeを指定して、利用可能なレポートフィールドのリストを取得します。
各レポートフィールドはフィールド名、フィールドデータタイプ、およびenum値をカプセル化します。

##### ＜リクエストサンプル＞
```json
{
  "reportType": "LANDING_PAGE_URL"
}
```

##### ＜レスポンスサンプル＞
※長くなるため、一部、省略しています。
```json
{
    "errors": null,
    "rid": "1",
    "rval": {
        "errors": null,
        "fields": [
            {
                "canFilter": true,
                "canSelect": true,
                "displayFieldNameEN": "Account ID",
                "displayFieldNameJA": "アカウントID",
                "fieldName": "ACCOUNT_ID",
                "fieldType": "STRING",
                "impossibleCombinationFields": null,
                "xmlAttributeName": "accountID"
            },
            ...
        ],
        "operationSucceeded": true
    }
}
```

#### 2.	レポートを作成
ReportDefinitionServiceのaddを使用します。以下の指定が必要です。
* レポートの名称
* 集計期間の設定
* 日本語/英語の指定
* 出力フォーマットの指定

##### ＜リクエストサンプル＞
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "dateRange": {
        "endDate": "20211231",
        "startDate": "20211101"
      },
      "fields": [
        "COST",
        "IMPS",
        "CLICKS",
        "CLICK_RATE",
        "AVG_CPC",
        "TRACKING_URL",
        "CONVERSIONS",
        "CONV_RATE",
        "CONV_VALUE",
        "COST_PER_CONV",
        "VALUE_PER_CONV",
        "NETWORK",
        "CLICK_TYPE",
        "DEVICE",
        "DAY",
        "DAY_OF_WEEK",
        "QUARTER",
        "YEAR",
        "MONTH",
        "WEEK",
        "HOUR_OF_DAY"
      ],
      "filters": [
        {
          "field": "COST",
          "filterOperator": "NOT_EQUALS",
          "values": [
            "100"
          ]
        }
      ],
      "reportCompressType": "ZIP",
      "reportDateRangeType": "CUSTOM_DATE",
      "reportDownloadEncode": "UTF8",
      "reportDownloadFormat": "CSV",
      "reportIncludeDeleted": "TRUE",
      "reportLanguage": "JA",
      "reportName": "Sample Report Definition",
      "reportType": "ACCOUNT",
      "sortFields": [
        {
          "field": "CLICKS",
          "reportSortType": "ASC"
        }
      ]
    }
  ]
}
```

##### ＜レスポンスサンプル＞

```json
{
  "errors": null,
  "rid": "398875d659ae490e14fd8354ff8ff1b6",
  "rval": {
    "values": [
      {
        "errors": null,
        "operationSucceeded": true,
        "reportDefinition": {
          "accountId": 11111111,
          "completeTime": null,
          "dateRange": {
            "endDate": "20211231",
            "startDate": "20211101"
          },
          "fields": [
            "COST",
            "IMPS",
            "CLICKS",
            "CLICK_RATE",
            "AVG_CPC",
            "TRACKING_URL",
            "CONVERSIONS",
            "CONV_RATE",
            "CONV_VALUE",
            "COST_PER_CONV",
            "VALUE_PER_CONV",
            "NETWORK",
            "CLICK_TYPE",
            "DEVICE",
            "DAY",
            "DAY_OF_WEEK",
            "QUARTER",
            "YEAR",
            "MONTH",
            "WEEK",
            "HOUR_OF_DAY"
          ],
          "filters": [
            {
              "field": "COST",
              "filterOperator": "NOT_EQUALS",
              "values": [
                "100"
              ]
            }
          ],
          "reportCompressType": "ZIP",
          "reportDateRangeType": "CUSTOM_DATE",
          "reportDecimalPartDisplayType": "SIMPLE_DISPLAY",
          "reportDownloadEncode": "UTF8",
          "reportDownloadFormat": "CSV",
          "reportIncludeDeleted": "TRUE",
          "reportJobErrorDetail": null,
          "reportJobId": 2222222222,
          "reportJobStatus": "WAIT",
          "reportLanguage": "JA",
          "reportName": "Sample Report Definition",
          "reportSkipColumnHeader": "FALSE",
          "reportSkipReportSummary": "FALSE",
          "reportType": "ACCOUNT",
          "requestTime": "2021/12/24 19:18:38",
          "sortFields": [
            {
              "field": "CLICKS",
              "reportSortType": "ASC"
            }
          ]
        }
      }
    ]
  }
}
```

#### 3.	レポート作成状況の確認
ReportDefinitionServiceのgetを使用します。<br>
作成状況の確認ができます。<br>
レスポンスのjobStatusがCOMPLETEDになったら、4に進みます。

##### ＜リクエストサンプル＞
```json
{
  "accountId": 11111111,
  "numberResults": 1,
  "reportJobIds": [
    2222222222
  ],
  "startIndex": 1
}
```

##### ＜レスポンスサンプル＞

```json
{
  "errors": null,
  "rid": "0865ecc73df3bec4b8cac750efde2668",
  "rval": {
    "totalNumEntries": 1,
    "values": [
      {
        "errors": null,
        "operationSucceeded": true,
        "reportDefinition": {
          "accountId": 11111111,
          "completeTime": "2021/12/24 19:18:43",
          "dateRange": {
            "endDate": "20211231",
            "startDate": "20211101"
          },
          "fields": [
            "COST",
            "IMPS",
            "CLICKS",
            "CLICK_RATE",
            "AVG_CPC",
            "TRACKING_URL",
            "CONVERSIONS",
            "CONV_RATE",
            "CONV_VALUE",
            "COST_PER_CONV",
            "VALUE_PER_CONV",
            "NETWORK",
            "CLICK_TYPE",
            "DEVICE",
            "DAY",
            "DAY_OF_WEEK",
            "QUARTER",
            "YEAR",
            "MONTH",
            "WEEK",
            "HOUR_OF_DAY"
          ],
          "filters": [
            {
              "field": "COST",
              "filterOperator": "NOT_EQUALS",
              "values": [
                "100"
              ]
            }
          ],
          "reportCompressType": "ZIP",
          "reportDateRangeType": "CUSTOM_DATE",
          "reportDecimalPartDisplayType": "SIMPLE_DISPLAY",
          "reportDownloadEncode": "UTF8",
          "reportDownloadFormat": "CSV",
          "reportIncludeDeleted": "TRUE",
          "reportJobErrorDetail": null,
          "reportJobId": 2222222222,
          "reportJobStatus": "COMPLETED",
          "reportLanguage": "JA",
          "reportName": "Sample Report Definition",
          "reportSkipColumnHeader": "FALSE",
          "reportSkipReportSummary": "FALSE",
          "reportType": "ACCOUNT",
          "requestTime": "2021/12/24 19:18:38",
          "sortFields": [
            {
              "field": "CLICKS",
              "reportSortType": "ASC"
            }
          ]
        }
      }
    ]
  }
}
```

#### 4.	レポートのダウンロード
ReportDefinitionServiceのdownloadを使用します。<br>
作成したレポートをダウンロードします。<br>

##### ＜リクエストサンプル＞
```json
{
  "accountId": 11111111,
  "reportJobId": 11111111
}
```

##### ＜レスポンスサンプル＞
※対象のデータがない場合、以下のようになります。<br>
```.csv
コスト,インプレッション数,クリック数,クリック率,平均CPC,トラッキングURL,コンバージョン数,コンバージョン率,コンバージョンの価値,コスト/コンバージョン数,価値/コンバージョン数,広告掲載方式の指定,クリック種別,デバイス,日,曜日,四半期,年間,毎月,毎週,時間
0,0,0,0,0,,0,0,0,0,0,,,,,,,,,,
```
