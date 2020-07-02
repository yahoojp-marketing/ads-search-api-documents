# エラーコード

### エラー処理概要
リクエストが成功した場合、検索広告APIは、Status: 200 OK、というHTTPステータスコードと、検索広告APIのレスポンスを返します。<br>
リクエストの処理中にエラーが発生した場合、検索広告APIは、エラーコードが含まれるメッセージを返します。

### エラーレスポンスサンプル

エラーレスポンスには、HTTPステータス、全体エラー、部分エラーがあります。<br>
以下で各レスポンスについて説明します。

#### HTTPステータス

リクエスト構文違反、システムエラー、認証エラーなどは、Status: 200 OK、以外のHTTPステータスコードが返却されます。<br>
例えば、アクセストークンの認証に失敗した場合、Status: 401 UnauthorizedのHTTPステータスコードと、以下のエラーコードが含まれるメッセージを返します。<br>

#### リクエスト
```json
{
  "accountIds": [
    11111111
  ],
  "numberResults": 0,
  "startIndex": 1
}
```

#### レスポンス
```json
{
    "rid": "178ed42a0e8f26acbb37ac2da2969bdd",
    "errors": [
        {
            "code": "0111",
            "message": "Authentication failed.",
            "details": []
        }
    ]
}
```
※その他のHTTPステータスは、APIリファレンスを参照してください。

#### 全体エラー
リクエストの制約などにより、リクエスト全体が失敗した場合は、Status: 200 OKのレスポンスコードが返されますが、全体エラーのレスポンスが返却されます。<br>
以下は、AccountService:get、で、`numberResults` の値（ページ数）が不正な場合のエラーレスポンス例です。

#### リクエスト
```json
{
  "accountIds": [
    11111111
  ],
  "numberResults": 0,
  "startIndex": 1
}
```

#### レスポンス
```json
{
    "rid": "02505e66279a0a103f05421a6529ac7b",
    "errors": [
        {
            "code": "0001",
            "message": "Invalid Request.",
            "details": [
                {
                    "requestKey": "numberResults",
                    "requestValue": "must be greater than or equal to 1"
                }
            ]
        }
    ]
}
```

#### 部分エラー
`operand` 内の各要素の制約などによりエラーが発生した場合は、Status: 200 OKのレスポンスコードが返されますが、部分エラーのレスポンスが返却されます。<br>
部分エラーは、各 `operand` ごとにエラーが発生したかについて返却します。<br>
なお、一回のリクエストで複数の `operand` を送るなど、複数の操作を要求するリクエストを送った場合、`operationSucceeded` の値が `true` と`false` が混在するエラーレスポンスになる場合もあります。<br>
<br>
以下は、ReportDefinitionService:add、で問題ない`operand（Sample Report Definition）`と、dateRange（レポート取得期間）に問題ある値を指定した`operand（Sample Report Definition2）`を、同時にリクエストしたときのレスポンス例です。

#### リクエスト
```json
{
  "accountId": 11111111,
  "operand": [
    {
      "fields": [
        "COST",
        "IMPS",
        "CLICKS"
      ],
      "reportCompressType": "ZIP",
      "reportDateRangeType": "TODAY",
      "reportLanguage": "JA",
      "reportName": "Sample Report Definition",
      "reportType": "ACCOUNT"
    },
    {
      "dateRange": {
        "endDate": "2019/09/01 12:00:00",
        "startDate": "2019/09/30 12:00:00"
      },
      "fields": [
        "COST",
        "IMPS",
        "CLICKS"
      ],
      "reportCompressType": "ZIP",
      "reportDateRangeType": "CUSTOM_DATE",
      "reportLanguage": "JA",
      "reportName": "Sample Report Definition2",
      "reportType": "ACCOUNT"
    }
  ]
}
```

#### レスポンス
```json
{
    "errors": null,
    "rid": "f42378455b9eaf72b7860c4a03ca0ba2",
    "rval": {
        "values": [
            {
                "errors": null,
                "operationSucceeded": true,
                "reportDefinition": {
                    "accountId": 11111111,
                    "completeTime": null,
                    "dateRange": null,
                    "fields": [
                        "COST",
                        "IMPS",
                        "CLICKS"
                    ],
                    "filters": null,
                    "reportCompressType": "ZIP",
                    "reportDateRangeType": "TODAY",
                    "reportDownloadEncode": "UTF-8",
                    "reportDownloadFormat": "CSV",
                    "reportIncludeDeleted": "TRUE",
                    "reportIncludeZeroImpressions": "FALSE",
                    "reportJobErrorDetail": null,
                    "reportJobId": 2568854952,
                    "reportJobStatus": "WAIT",
                    "reportLanguage": "JA",
                    "reportName": "Sample Report Definition",
                    "reportType": "ACCOUNT",
                    "requestTime": "2020/06/18 15:55:28",
                    "sortFields": null
                }
            },
            {
                "errors": [
                    {
                        "code": "F0001",
                        "message": "Invalid format.",
                        "details": [
                            {
                                "requestKey": "dateRange/startDate",
                                "requestValue": "2019/09/30 12:00:00"
                            }
                        ]
                    },
                    {
                        "code": "F0001",
                        "message": "Invalid format.",
                        "details": [
                            {
                                "requestKey": "dateRange/endDate",
                                "requestValue": "2019/09/01 12:00:00"
                            }
                        ]
                    },
                    {
                        "code": "RL001",
                        "message": "Invalid relation.",
                        "details": [
                            {
                                "requestKey": "reportDateRangeType",
                                "requestValue": "CUSTOM_DATE"
                            },
                            {
                                "requestKey": "dateRange/startDate",
                                "requestValue": "2019/09/30 12:00:00"
                            },
                            {
                                "requestKey": "dateRange/endDate",
                                "requestValue": "2019/09/01 12:00:00"
                            }
                        ]
                    }
                ],
                "operationSucceeded": false,
                "reportDefinition": null
            }
        ]
    }
}
```

### エラーコード（全サービス共通エラー）

コード                   | メッセージ  | 説明
------------------------ | ----------- | -------------------------------------------------------
F0001 | Invalid format.  | 値の形式が不正です。
R0001 | Require.  | 必須です。
V0001 | Invalid value.  | 値が無効です。
L0001 | Lower list size. | 配列の要素数が下限値を下回っています。
L0002 | Over list size. | 配列の要素数が上限値を超過しています。
U0002 | Invalid url. | アップロードURLまたはダウンロードURLが不正です。
S0001 | Invalid Status. | ステータスが無効です。
I0001 | Deactivated Id. | IDが無効です。
D0001 | Duplicate. | 一意な値が重複しています。
RL001 | Invalid relation. | リクエストの関連性が矛盾しています。<br> たとえば、開始＞終了の日付指定を行なっているなど
LT001 | Over limit. | 登録できる上限値を超過しています。
0001 | Invalid Request. | さまざまな要因が考えられます。<br>主な要因は、パラメータの値が不正か、誤りがあるためにオペレーションが完了できません。
0002 | An internal error has occurred.  | 内部エラーが発生しました。再度操作を実行してください。 <br>もし、問題が解決しない場合は、お問い合わせページをご利用ください。
0003 | Frequency limit exceeded. Please try your request again later | アクセス頻度が上限値に達しました。時間をおいて再度実行してください。
0004 | URL not found. | URLが不正です。
0005 | Bad request. | リクエストが不正です。
0098 | Permission denied. | 権限がありません。
0099 | Out of service. | APIがメンテナンス中、またはご利用できません。

※各Service固有のエラーは、[APIリファレンス](http://ads-developers.yahoo.co.jp/reference/ads-search-api/)を参照してください。
