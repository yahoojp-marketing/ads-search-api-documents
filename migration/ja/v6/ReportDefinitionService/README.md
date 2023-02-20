# ReportDefinitionService v6 移行ガイド

Yahoo!検索広告v6 ReportDefinitionServiceでは一部のレポート出力項目に変更があります。  
本移行ガイドではv5 ReportDefinitionServiceからv6 ReportDefinitionServiceへの移行に必要な対応について説明します。

## 目次

- [変更内容](#変更内容)
  - [ReportDefinitionService/add](#reportdefinitionserviceadd)
  - [ReportDefinitionService/download](#reportdefinitionservicedownload)
- [Q&A](#qa)
  - [レポート出力項目の詳細な変更点を教えて下さい。](#%E3%83%AC%E3%83%9D%E3%83%BC%E3%83%88%E5%87%BA%E5%8A%9B%E9%A0%85%E7%9B%AE%E3%81%AE%E8%A9%B3%E7%B4%B0%E3%81%AA%E5%A4%89%E6%9B%B4%E7%82%B9%E3%82%92%E6%95%99%E3%81%88%E3%81%A6%E4%B8%8B%E3%81%95%E3%81%84)
  - [QPSに変更はありますか？](#qps%E3%81%AB%E5%A4%89%E6%9B%B4%E3%81%AF%E3%81%82%E3%82%8A%E3%81%BE%E3%81%99%E3%81%8B)
  - [他にv6で変更されたものはありますか？](#%E4%BB%96%E3%81%ABv6%E3%81%A7%E5%A4%89%E6%9B%B4%E3%81%95%E3%82%8C%E3%81%9F%E3%82%82%E3%81%AE%E3%81%AF%E3%81%82%E3%82%8A%E3%81%BE%E3%81%99%E3%81%8B)

## 変更内容

v6 ReportDefinitionServiceでは、一部のレポートタイプとレポート出力項目（フィールド）に変更があります。

### ReportDefinitionService/add

#### 変更点

- レポート出力項目（フィールド）の変更
  - **詳細は[レポートタイプごとの変更点](ReportType.md)をご参照ください**
- 次のレポートタイプはv6以降のバージョンで廃止されます
  - `TARGET_LIST`
  - `AD_CUSTOMIZERS`
  - 代替となるレポートタイプについては[レポートタイプごとの変更点](ReportType.md)をご参照ください
- reportIncludeZeroImpressionsフィールドはv6以降のバージョンで廃止されます。
  - 従来のバージョンでは、デフォルト（`reportIncludeZeroImpressions`が`false`の場合）で実績がすべて0の行は除外されていました。
  - v6以降のバージョンでは実績のない行も含めて出力されるため、データが大量となり、レポート取得時にエラーが発生する可能性があります。
  - v6以降のバージョンで実績のある行のみをレポートに出力するためには、フィルタ条件でIMPS、ALL_CONV等の実績に関わる項目を1以上に設定してください。
```r
#リクエスト例
{
  "accountId": 111111,
  "operand": [
    {
      "fields": [
        "ACCOUNT_NAME",
        "IMPS",
        "AVG_CPC",
        "TRACKING_URL"
      ],
      "filters": [
        "field": "IMPS",
        "filterOperator": "GREATER_THAN_EQUALS",
        "values": [
          "1"
        ]
      ],
      "reportDateRangeType": "YESTERDAY",
      "reportIncludeDeleted": "TRUE",
      "reportLanguage": "JA",
      "reportName": "Report",
      "reportType": "AD"
    }
  ]
}
```

### ReportDefinitionService/download

#### 変更点

- 出力方式変更
  - `CLICK_RATE`など型がDOUBLEのフィールドにおけるゼロパディング廃止 **`1.0000` → `1`**
  - `CLICK_RATE`など型がDOUBLEのフィールドにおいて、小数点が4桁まで表示（デフォルト設定を変更することで最大16桁まで表示可能）
  - フィルター指定時に除算を含むフィールドはその分母と分子がフィールドに指定されていた場合、合計行が計算されますが、分母と分子がフィールドに含まれていない場合、合計行は0になります
  - 値が存在しない場合の表記が以下のように変更されます。

    | | LONG | DOUBLE | STRING ※ | ENUM |
    | --- | --- | --- | --- | --- |
    | 変更前 | 0 or -- | 0 or -- | -- | --　(またはデフォルト値) |
    | 変更後 | 0 | 0 | "" | "" |

    （※ ACCOUNT_ID、ACCOUNT_NAMEに関しては、それぞれアカウントIDとアカウント名が入り、「--」、「""」にはなりません。）

上記変更点を含めたレポートタイプごとの詳細な差分は[レポートタイプごとの変更点](ReportType.md)をご参照ください。

#### レスポンス例

v5とv6の/ReportDefinitionService/downloadへのリクエスト例です。

```r
#v5レポート取得例
アカウント名,インプレッション数,平均CPC,デバイスをまたいだコンバージョン数,トラッキングURL,広告掲載方式の指定
サンプルアカウント,159116,85.4555,--,http://www.example.com,ウェブ検索
サンプルアカウント,43,12.6000,--,--,その他の広告掲載方式
サンプルアカウント,159159,85.5434,--,--,--
```

```r
#v6レポート取得例
アカウント名,インプレッション数,平均CPC,デバイスをまたいだコンバージョン数,トラッキングURL,広告掲載方式の指定
サンプルアカウント,159116,85.4555,0,http://www.example.com,ウェブ検索
サンプルアカウント,43,12.6,0,,その他の広告掲載方式
サンプルアカウント,159159,85.5434,0,,
```

## Q&A

### レポート出力項目の詳細な変更点を教えて下さい。

[レポートタイプごとの変更点](ReportType.md)をご参照ください。

### QPSに変更はありますか？

QPSには変更はありません。   
QPSについての詳しい説明は[リクエストの制約（QPS）](https://ads-developers.yahoo.co.jp/ja/ads-api/developers-guide/qps.html)をご参照ください。

### 他にv6で変更されたものはありますか？

レポート作成時にヘッダー行、トータル行、小数項目の表示形式を選択することができるようになりました。  
ヘッダー行は`reportSkipColumnHeader`、トータル行は`reportSkipReportSummary`、小数項目は`reportDecimalPartDisplayType`のフィールドで指定できます。  
指定しない場合はこれまでのバージョンと挙動は変わりません。

詳しくは[v6 ReportDefinitionService/add のAPIリファレンス](https://ads-developers.yahoo.co.jp/reference/ads-search-api/v6/ReportDefinitionService/add/)をご参照ください。
