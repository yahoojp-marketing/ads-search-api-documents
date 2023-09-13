# コンバージョントラッキング機能
## コンバージョンとは
広告をクリックしたユーザーが、何らかの「成果」となる行動をとった数です。これを計測することで、広告がどの程度成果を上げているかなどを確認できます。<br>
詳しくは以下のヘルプをご参照ください。<br>
・<a href="https://ads-help.yahoo-net.jp/s/article/H000045014?language=ja">コンバージョン測定とは</a>

## 検索広告API での実施方法
検索広告APIでは、コンバージョントラッカー情報（コンバージョン測定タグおよび、タグごとのパフォーマンスデータ）の取得および追加・更新を行うために、ConversionTrackerService、を使用します。<br>
本サービスを利用することで、検索広告で掲載されている広告からのコンバージョン数（商品の購入や会員登録、資料請求などサイト上で何らかの成約に至った件数）を取得することができ、広告がどの程度成果を上げているかなどを確認できます。<br>
コンバージョンタグは広告管理ツールとAPIで共有しています。

## シナリオ
A社は商品B（1万円）を販売しているが、ウェブページでコンバージョンを計測するための、コンバージョントラッカーを作成する。

<table class="standard">
  <tr>
　　<th>項目</th>
　　<th>値</th>
　　<th>項目の説明</th>
　</tr>
　<tr>
　　<td>category</td>
　　<td>PURCHASE（購入/販売）</td>
　　<td>コンバージョントラッカー情報のカテゴリ</td>
　</tr>
　<tr>
　　<td>conversionTrackerName</td>
　　<td>（分かりやすい名称を）</td>
　　<td>コンバージョントラッカーの名称</td>
　</tr>
　<tr>
　　<td>conversionTrackerType</td>
　　<td>WEB_CONVERSION</td>
　　<td>コンバージョンの種別</td>
　</tr>
　<tr>
　　<td>measurementPeriod</td>
　　<td>30</td>
　　<td>コンバージョン計測期間（●日）</td>
　</tr>
　<tr>
　　<td>status</td>
　　<td>ENABLED（ウェブページへのアクセスを記録する）</td>
　　<td>コンバージョントラッカー情報のステータス</td>
　</tr>
　<tr>
　　<td>userRevenueValue</td>
　　<td>10000</td>
　　<td>売上金額が固定のときの、1コンバージョンの売上（●円）※商品Bの値段</td>
　</tr>
　<tr>
　　<td>markupLanguage（webConversion）</td>
　　<td>HTML</td>
　　<td>スニペットの記述に使用するマークアップ言語</td>
　</tr>
　<tr>
　　<td>trackingCodeType（webConversion）</td>
　　<td>WEBPAGE</td>
　　<td>ウェブページのトラッキングタイプ</td>
　</tr>
</table>
<br>

#### 1.	トラッカー情報の登録
はじめに、ConversionTrackerService:addを使い、コンバージョントラッカー情報を追加します。

##### リクエストサンプル
```json
{
  "accountId": 111111,
  "operand": [
    {
      "category": "PURCHASE",
      "conversionTrackerName": "Pro_B_CV",
      "conversionTrackerType": "WEB_CONVERSION",
      "measurementPeriod": 30,
      "status": "ENABLED",
      "userRevenueValue": "10000",
      "webConversion": {
        "markupLanguage": "HTML",
        "trackingCodeType": "WEBPAGE"
      }
    }
  ]
}
```

##### レスポンスサンプル
※snippet（webConversion）と、advancedSnippet（webConversion）のレスポンスは、ConversionTrackerService:getで確認してください。
```json
{
    "errors": null,
    "rid": "f7eaf398417b6eea34b1274ce683469d",
    "rval": {
        "values": [
            {
                "conversionTracker": {
                    "accountId": 111111,
                    "allConversionValue": null,
                    "allConversions": null,
                    "appConversion": null,
                    "category": "PURCHASE",
                    "conversionCountingType": "MANY_PER_CLICK",
                    "conversionTrackerId": 222222,
                    "conversionTrackerName": "Pro_B_CV",
                    "conversionTrackerType": "WEB_CONVERSION",
                    "conversionValue": null,
                    "conversions": null,
                    "excludeFromBidding": "FALSE",
                    "measurementPeriod": 30,
                    "mostRecentConversionDate": null,
                    "status": "ENABLED",
                    "userRevenueValue": "10000",
                    "webConversion": {
                        "markupLanguage": "HTML",
                        "snippet": null,
                        "advancedSnippet": null,
                        "trackingCodeType": "WEBPAGE"
                    }
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
<br>

#### 2. コンバージョン計測タグの取得
次に、ConversionTrackerService:getを使い、先ほど登録したコンバージョン計測タグを取得します。<br>
※コンバージョン測定タグの、snippet（webConversion）※従来版、advancedSnippet（webConversion）※リニューアル版、は、ここで確認してください。<br>
※advancedSnippetを使用する場合、サイトジェネラルタグも必要です。詳しくは以下のヘルプをご参照ください。<br>
・<a href="https://ads-help.yahoo-net.jp/s/article/H000044574?language=ja">サイトジェネラルタグについて</a>

##### リクエストサンプル
```json
{
  "accountId": 111111,
  "conversionTrackerIds": [
    222222
  ],
  "numberResults": 1,
  "startIndex": 1,
  "statuses": [
    "ENABLED"
  ],
  "trackingCodeTypes": [
    "WEBPAGE"
  ]
}
```

##### レスポンスサンプル
```json
{
    "errors": null,
    "rid": "180b348e3630b1feef3a9ef24546e488",
    "rval": {
        "totalAllConversionValue": "0",
        "totalAllConversions": 0,
        "totalConversionValue": "0",
        "totalConversions": 0,
        "totalNumEntries": 1,
        "values": [
            {
                "conversionTracker": {
                    "accountId": 111111,
                    "allConversionValue": null,
                    "allConversions": null,
                    "appConversion": null,
                    "category": "PURCHASE",
                    "conversionCountingType": "MANY_PER_CLICK",
                    "conversionTrackerId": 222222,
                    "conversionTrackerName": "Pro_B_CV",
                    "conversionTrackerType": "WEB_CONVERSION",
                    "conversionValue": null,
                    "conversions": null,
                    "excludeFromBidding": "FALSE",
                    "measurementPeriod": 30,
                    "mostRecentConversionDate": null,
                    "status": "ENABLED",
                    "userRevenueValue": "10000",
                    "webConversion": {
                        "markupLanguage": "HTML",
                        "snippet": "<!-- Yahoo Code for your Conversion Page -->\n<script type=\"text/javascript\">\n    /* <![CDATA[ */\n    var yahoo_conversion_id = 1000000407;\n    var yahoo_conversion_label = \"S7vjCPKvk9oBEJ7fgOQD\";\n    var yahoo_conversion_value = 10000;\n    /* ]]> */\n</script>\n<script type=\"text/javascript\" src=\"https://s.yimg.jp/images/listing/tool/cv/conversion.js\">\n</script>\n<noscript>\n    <div style=\"display:inline;\">\n        <img height=\"1\" width=\"1\" style=\"border-style:none;\" alt=\"\" src=\"https://b91.yahoo.co.jp/pagead/conversion/1000000407/?value=10000&label=S7vjCPKvk9oBEJ7fgOQD&guid=ON&script=0&disvt=true\"/>\n    </div>\n</noscript>",
                        "advancedSnippet": "<script async>\nytag({\n  \"type\": \"yss_conversion\",\n  \"config\": {\n    \"yahoo_conversion_id\": \"1000000407\",\n    \"yahoo_conversion_label\": \"S7vjCPKvk9oBEJ7fgOQD\",\n    \"yahoo_conversion_value\": \"10000\"\n  }\n});\n</script>",
                        "trackingCodeType": "WEBPAGE"
                    }
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
<br>

#### 3. タグをウェブサイトに埋め込み、計測を開始する
上記の、ConversionTrackerService:get、で取得した、snippet（webConversion）、advancedSnippet（webConversion）を、ウェブサイトに埋め込んで、計測を開始します。<br><br>

#### 4. コンバージョンの計測結果を取得する
再び、ConversionTrackerService:getを使い、コンバージョンの計測結果を取得します。

##### リクエストサンプル
```json
{
  "accountId": 111111,
  "conversionTrackerIds": [
    222222
  ],
  "numberResults": 1,
  "startIndex": 1,
  "statuses": [
    "ENABLED"
  ],
  "trackingCodeTypes": [
    "WEBPAGE"
  ]
}
```

##### レスポンスサンプル
```json
{
    "errors": null,
    "rid": "180b348e3630b1feef3a9ef24546e488",
    "rval": {
        "totalAllConversionValue": "10000000",
        "totalAllConversions": 1000,
        "totalConversionValue": "100000000",
        "totalConversions": 10000,
        "totalNumEntries": 1,
        "values": [
            {
                "conversionTracker": {
                    "accountId": 111111,
                    "allConversionValue": 10000000,
                    "allConversions": 1000,
                    "appConversion": null,
                    "category": "PURCHASE",
                    "conversionCountingType": "MANY_PER_CLICK",
                    "conversionTrackerId": 222222,
                    "conversionTrackerName": "Pro_B_CV",
                    "conversionTrackerType": "WEB_CONVERSION",
                    "conversionValue": 100000000,
                    "conversions": 10000,
                    "excludeFromBidding": "FALSE",
                    "measurementPeriod": 30,
                    "mostRecentConversionDate": null,
                    "status": "ENABLED",
                    "userRevenueValue": "10000",
                    "webConversion": {
                        "markupLanguage": "HTML",
                        "snippet": "<!-- Yahoo Code for your Conversion Page -->\n<script type=\"text/javascript\">\n    /* <![CDATA[ */\n    var yahoo_conversion_id = 1000000407;\n    var yahoo_conversion_label = \"S7vjCPKvk9oBEJ7fgOQD\";\n    var yahoo_conversion_value = 10000;\n    /* ]]> */\n</script>\n<script type=\"text/javascript\" src=\"https://s.yimg.jp/images/listing/tool/cv/conversion.js\">\n</script>\n<noscript>\n    <div style=\"display:inline;\">\n        <img height=\"1\" width=\"1\" style=\"border-style:none;\" alt=\"\" src=\"https://b91.yahoo.co.jp/pagead/conversion/1000000407/?value=10000&label=S7vjCPKvk9oBEJ7fgOQD&guid=ON&script=0&disvt=true\"/>\n    </div>\n</noscript>",
                        "advancedSnippet": "<script async>\nytag({\n  \"type\": \"yss_conversion\",\n  \"config\": {\n    \"yahoo_conversion_id\": \"1000000407\",\n    \"yahoo_conversion_label\": \"S7vjCPKvk9oBEJ7fgOQD\",\n    \"yahoo_conversion_value\": \"10000\"\n  }\n});\n</script>",
                        "trackingCodeType": "WEBPAGE"
                    }
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
<br>

#### 5.	トラッカー情報の更新
そして、ConversionTrackerService:setを使い、先ほど登録したコンバージョントラッカー情報を更新します。<br>
以下では、コンバージョントラッカー情報のカテゴリを、PURCHASE（販売）からPAGE_VIEW（主要なページの閲覧）に更新しています。

##### リクエストサンプル
```json
{
  "accountId": 111111,
  "operand": [
    {
      "category": "PAGE_VIEW",
      "conversionTrackerId": 222222,
      "conversionTrackerType": "WEB_CONVERSION"
    }
  ]
}
```

##### レスポンスサンプル
```json
{
    "errors": null,
    "rid": "5b5d34b5cd8238352127e418b2b4bacb",
    "rval": {
        "values": [
            {
                "conversionTracker": {
                    "accountId": 111111,
                    "allConversionValue": 10000000,
                    "allConversions": 1000,
                    "appConversion": null,
                    "category": "PAGE_VIEW",
                    "conversionCountingType": "MANY_PER_CLICK",
                    "conversionTrackerId": 222222,
                    "conversionTrackerName": "Pro_B_CV",
                    "conversionTrackerType": "WEB_CONVERSION",
                    "conversionValue": 100000000,
                    "conversions": 10000,
                    "excludeFromBidding": "FALSE",
                    "measurementPeriod": 30,
                    "mostRecentConversionDate": null,
                    "status": "ENABLED",
                    "userRevenueValue": "10000",
                    "webConversion": {
                        "markupLanguage": "HTML",
                        "snippet": "<!-- Yahoo Code for your Conversion Page -->\n<script type=\"text/javascript\">\n    /* <![CDATA[ */\n    var yahoo_conversion_id = 1000000407;\n    var yahoo_conversion_label = \"S7vjCPKvk9oBEJ7fgOQD\";\n    var yahoo_conversion_value = 10000;\n    /* ]]> */\n</script>\n<script type=\"text/javascript\" src=\"https://s.yimg.jp/images/listing/tool/cv/conversion.js\">\n</script>\n<noscript>\n    <div style=\"display:inline;\">\n        <img height=\"1\" width=\"1\" style=\"border-style:none;\" alt=\"\" src=\"https://b91.yahoo.co.jp/pagead/conversion/1000000407/?value=10000&label=S7vjCPKvk9oBEJ7fgOQD&guid=ON&script=0&disvt=true\"/>\n    </div>\n</noscript>",
                        "advancedSnippet": "<script async>\nytag({\n  \"type\": \"yss_conversion\",\n  \"config\": {\n    \"yahoo_conversion_id\": \"1000000407\",\n    \"yahoo_conversion_label\": \"S7vjCPKvk9oBEJ7fgOQD\",\n    \"yahoo_conversion_value\": \"10000\"\n  }\n});\n</script>",
                        "trackingCodeType": "WEBPAGE"
                    }
                },
                "errors": null,
                "operationSucceeded": true
            }
        ]
    }
}
```
