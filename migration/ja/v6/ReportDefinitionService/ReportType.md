# レポートタイプごとの変更点

Yahoo!検索広告v6 ReportDefinitionServiceでのレポートタイプごとのレポート出力項目（フィールド）の変更点です。

## 目次

- [アカウントレポート: `ACCOUNT`](#アカウントレポート-account)
- [キャンペーンレポート: `CAMPAIGN`](#キャンペーンレポート-campaign)
- [広告グループレポート: `ADGROUP`](#広告グループレポート-adgroup)
- [広告レポート: `AD`](#広告レポート-ad)
- [キーワードレポート: `KEYWORDS`](#キーワードレポート-keywords)
- [検索クエリーレポート: `SEARCH_QUERY`](#検索クエリーレポート-search_query)
- [地域別レポート: `GEO`](#地域別レポート-geo)
- [広告表示オプションレポート: `FEED_ITEM`](#広告表示オプションレポート-feed_item)
- [地域ターゲティングレポート: `GEO_TARGET`](#地域ターゲティングレポート-geo_target)
- [曜日・時間帯ターゲティングレポート: `SCHEDULE_TARGET`](#曜日時間帯ターゲティングレポート-schedule_target)
- [自動入札レポート: `BID_STRATEGY`](#自動入札レポート-bid_strategy)
- [ターゲットリストレポート: `TARGET_LIST`](#ターゲットリストレポート-target_list)
- [キャンペーンターゲットリストレポート: `CAMPAIGN_TARGET_LIST`](#キャンペーンターゲットリストレポート-campaign_target_list)
- [広告グループターゲットリストレポート: `ADGROUP_TARGET_LIST`](#広告グループターゲットリストレポート-adgroup_target_list)
- [検索クエリーレポート（動的検索連動型広告）: `KEYWORDLESS_QUERY`](#検索クエリーレポート動的検索連動型広告-keywordless_query)
- [データ自動挿入レポート: `AD_CUSTOMIZERS`](#データ自動挿入レポート-ad_customizers)
- [ページフィードターゲティングレポート: `WEBPAGE_CRITERION`](#ページフィードターゲティングレポート-webpage_criterion)
- [最終リンク先URLレポート: `LANDING_PAGE_URL`](#最終リンク先URLレポート-landing_page_url)
- [入札価格調整率レポート: `BID_MODIFIER`](#入札価格調整率レポート-bid_modifier)

## アカウントレポート: `ACCOUNT`

| フィールド | 変更内容 |
| --- | --- |
| AVG_DELIVER_RANK | 削除されます |
| EXACT_MATCH_IMPRESSION_SHARE | 値が0.1より小さい場合のレポートの値が0.1から0.0999になります<br/>値が0.9より大きい場合のレポートの値が0.9から0.9001になります |
| IMPRESSION_SHARE | 値が0.1より小さい場合のレポートの値が0.1から0.0999になります |
| BUDGET_LOST_IMPRESSION_SHARE | 値が0.9より大きい場合のレポートの値が0.9から0.9001になります |
| QUALITY_LOST_IMPRESSION_SHARE | 値が0.9より大きい場合のレポートの値が0.9から0.9001になります |
| AVG_CPC | 桁数処理が切り捨てから四捨五入になります |
| COST_PER_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| COST_PER_ALL_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| ALL_CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ALL_CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| DEVICE | レポートの値が変わります。詳細は下記をご確認下さい |

DEVICEの変更内容

| 変更前（日本語表示名称） | 変更前（英語表示名称） | 変更後（日本語表示名称） | 変更後（英語表示名称） |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

### 組み合わせ不可項目の変更点
2021年9月13日に掲載されるv6のAPIリファレンスをご確認ください。

## キャンペーンレポート: `CAMPAIGN`
### フィールドごとの変更点

| フィールド | 変更内容 |
| --- | --- |
| AVG_DELIVER_RANK | 削除されます |
| CAMPAIGN_MOBILE_BID_MODIFIER | 削除されます。入札価格調整率レポートをご利用ください。 |
| CAMPAIGN_DESKTOP_BID_MODIFIER | 削除されます。入札価格調整率レポートをご利用ください。 |
| CAMPAIGN_TABLET_BID_MODIFIER | 削除されます。入札価格調整率レポートをご利用ください。 |
| EXACT_MATCH_IMPRESSION_SHARE | 値が0.1より小さい場合のレポートの値が0.1から0.0999になります<br/>値が0.9より大きい場合のレポートの値が0.9から0.9001になります |
| IMPRESSION_SHARE | 値が0.1より小さい場合のレポートの値が0.1から0.0999になります |
| SEARCH_ABSOLUTE_TOP_IMPRESSION_SHARE | 値が0.1より小さい場合のレポートの値が0.1から0.0999になります |
| SEARCH_BUDGET_LOST_ABSOLUTE_TOP_IMPRESSION_SHARE | 値が0.1より小さい場合のレポートの値が0.1から0.0999になります |
| SEARCH_BUDGET_LOST_TOP_IMPRESSION_SHARE | 値が0.1より小さい場合のレポートの値が0.1から0.0999になります |
| BUDGET_LOST_IMPRESSION_SHARE | 値が0.9より大きい場合のレポートの値が0.9から0.9001になります |
| QUALITY_LOST_IMPRESSION_SHARE | 値が0.9より大きい場合のレポートの値が0.9から0.9001になります |
| EXACT_MATCH_IMPRESSION_SHARE | 値が0.9より大きい場合のレポートの値が0.9から0.9001になります |
| AVG_CPC | 桁数処理が切り捨てから四捨五入になります |
| COST_PER_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| COST_PER_ALL_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| DEVICE | レポートの値が変わります。詳細は下記をご確認下さい |
| LABELS_JSON | 【変更前】"[""ラベル1"",""ラベル2""]" <br/>【変更後】"[{""labelId"":""1"",""value"":""ラベル1""},{""labelId"":""2"",""value"":""ラベル2""}]" |
| TOP_IMPRESSION_PERCENTAGE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| SEARCH_TOP_IMPRESSION_SHARE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ABSOLUTE_TOP_IMPRESSION_PERCENTAGE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| SEARCH_RANK_LOST_TOP_IMPRESSION_SHARE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| SEARCH_RANK_LOST_ABSOLUTE_TOP_IMPRESSION_SHARE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| SEARCH_BUDGET_LOST_TOP_IMPRESSION_SHARE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| SEARCH_BUDGET_LOST_ABSOLUTE_TOP_IMPRESSION_SHARE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ALL_CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ALL_CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |

DEVICEの変更内容の詳細

| 変更前（日本語表示名称） | 変更前（英語表示名称） | 変更後（日本語表示名称） | 変更後（英語表示名称） |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

### 組み合わせ不可項目の変更点
2021年9月13日に掲載されるv6のAPIリファレンスをご確認ください。

## 広告グループレポート: `ADGROUP`
### フィールドごとの変更点

| フィールド | 変更内容 |
| --- | --- |
| AVG_DELIVER_RANK | 削除されます |
| ADGROUP_MOBILE_BID_MODIFIER | 削除されます。入札価格調整率レポートをご利用ください。 |
| ADGROUP_DESKTOP_BID_MODIFIER | 削除されます。入札価格調整率レポートをご利用ください。 |
| ADGROUP_TABLET_BID_MODIFIER | 削除されます。入札価格調整率レポートをご利用ください。 |
| EXACT_MATCH_IMPRESSION_SHARE | 値が0.1より小さい場合のレポートの値が0.1から0.0999になります<br/>値が0.9より大きい場合のレポートの値が0.9から0.9001になります |
| IMPRESSION_SHARE | 値が0.1より小さい場合のレポートの値が0.1から0.0999になります |
| SEARCH_ABSOLUTE_TOP_IMPRESSION_SHARE | 値が0.1より小さい場合のレポートの値が0.1から0.0999になります |
| SEARCH_BUDGET_LOST_ABSOLUTE_TOP_IMPRESSION_SHARE | 値が0.1より小さい場合のレポートの値が0.1から0.0999になります |
| SEARCH_BUDGET_LOST_TOP_IMPRESSION_SHARE | 値が0.1より小さい場合のレポートの値が0.1から0.0999になります |
| BUDGET_LOST_IMPRESSION_SHARE | 値が0.9より大きい場合のレポートの値が0.9から0.9001になります |
| QUALITY_LOST_IMPRESSION_SHARE | 値が0.9より大きい場合のレポートの値が0.9から0.9001になります |
| EXACT_MATCH_IMPRESSION_SHARE | 値が0.9より大きい場合のレポートの値が0.9から0.9001になります |
| AVG_CPC | 桁数処理が切り捨てから四捨五入になります |
| COST_PER_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| COST_PER_ALL_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| DEVICE | レポートの値が変わります。詳細は下記をご確認下さい |
| LABELS_JSON | 【変更前】"[""ラベル1"",""ラベル2""]" <br/>【変更後】"[{""labelId"":""1"",""value"":""ラベル1""},{""labelId"":""2"",""value"":""ラベル2""}]" |
| TOP_IMPRESSION_PERCENTAGE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| SEARCH_TOP_IMPRESSION_SHARE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ABSOLUTE_TOP_IMPRESSION_PERCENTAGE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| SEARCH_RANK_LOST_TOP_IMPRESSION_SHARE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| SEARCH_RANK_LOST_ABSOLUTE_TOP_IMPRESSION_SHARE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| SEARCH_BUDGET_LOST_TOP_IMPRESSION_SHARE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| SEARCH_BUDGET_LOST_ABSOLUTE_TOP_IMPRESSION_SHARE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ALL_CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ALL_CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |

DEVICEの変更内容の詳細

| 変更前（日本語表示名称） | 変更前（英語表示名称） | 変更後（日本語表示名称） | 変更後（英語表示名称） |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

### 組み合わせ不可項目の変更点
2021年9月13日に掲載されるv6のAPIリファレンスをご確認ください。

## 広告レポート: `AD`
### フィールドごとの変更点

| フィールド | 変更内容 |
| --- | --- |
| AVG_DELIVER_RANK | 削除されます |
| TITLE | 削除されます |
| DESC | 削除されます |
| DESCRIPTION | 削除されます |
| AVG_CPC | 桁数処理が切り捨てから四捨五入になります |
| COST_PER_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| COST_PER_ALL_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| DEVICE | レポートの値が変わります。詳細は下記をご確認下さい |
| LABELS_JSON | 【変更前】"[""ラベル1"",""ラベル2""]" <br/>【変更後】"[{""labelId"":""1"",""value"":""ラベル1""},{""labelId"":""2"",""value"":""ラベル2""}]" |
| TOP_IMPRESSION_PERCENTAGE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ABSOLUTE_TOP_IMPRESSION_PERCENTAGE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| LANDING_PAGE_URL | フィールドの名称が変わります。詳細は下記をご確認下さい |
| LANDING_PAGE_URL_SMARTPHONE | フィールドの名称が変わります。詳細は下記をご確認下さい |
| ALL_CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ALL_CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |

DEVICEの変更内容の詳細

| 変更前（日本語表示名称） | 変更前（英語表示名称） | 変更後（日本語表示名称） | 変更後（英語表示名称） |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

LANDING_PAGE_URLの変更内容の詳細

|  | 変更前 | 変更後 |
| --- | --- | --- |
| ENUM | LANDING_PAGE_URL | FINAL_URL |
| 日本語表示名称 | 最終リンク先URL | 最終リンク先URL |
| 英語表示名称 | Landing Page URL | Final URL |

LANDING_PAGE_URL_SMARTPHONEの変更内容の詳細

|  | 変更前 | 変更後 |
| --- | --- | --- |
| ENUM | LANDING_PAGE_URL_SMARTPHONE | FINAL_URL_SMARTPHONE |
| 日本語表示名称 | 最終リンク先URL（スマートフォン） | スマートフォン向けURL |
| 英語表示名称 | Landing Page URL (Smartphone) | Smartphone final URL |

### 組み合わせ不可項目の変更点
2021年9月13日に掲載されるv6のAPIリファレンスをご確認ください。

### その他
出力するフィールドにAD_KEYWORD_IDを指定した場合、広告タイプ:動的検索連動型広告の行は出力されません。
広告レポートで広告タイプ:動的検索連動型広告の行を出力したい場合は、AD_KEYWORD_IDを含めずにレポートを作成してください。

## キーワードレポート: `KEYWORDS`
### フィールドごとの変更点

| フィールド | 変更内容 |
| --- | --- |
| AVG_DELIVER_RANK | 削除されます |
| EXACT_MATCH_IMPRESSION_SHARE | 値が0.1より小さい場合のレポートの値が0.1から0.0999になります<br/>値が0.9より大きい場合のレポートの値が0.9から0.9001になります |
| IMPRESSION_SHARE | 値が0.1より小さい場合のレポートの値が0.1から0.0999になります |
| SEARCH_ABSOLUTE_TOP_IMPRESSION_SHARE | 値が0.1より小さい場合のレポートの値が0.1から0.0999になります |
| SEARCH_BUDGET_LOST_ABSOLUTE_TOP_IMPRESSION_SHARE | 値が0.1より小さい場合のレポートの値が0.1から0.0999になります |
| SEARCH_BUDGET_LOST_TOP_IMPRESSION_SHARE | 値が0.1より小さい場合のレポートの値が0.1から0.0999になります |
| QUALITY_LOST_IMPRESSION_SHARE | 値が0.9より大きい場合のレポートの値が0.9から0.9001になります |
| AVG_CPC | 桁数処理が切り捨てから四捨五入になります |
| COST_PER_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| COST_PER_ALL_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| DEVICE | レポートの値が変わります。詳細は下記をご確認下さい |
| LABELS_JSON | 【変更前】"[""ラベル1"",""ラベル2""]" <br/>【変更後】"[{""labelId"":""1"",""value"":""ラベル1""},{""labelId"":""2"",""value"":""ラベル2""}]" |
| TOP_IMPRESSION_PERCENTAGE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| SEARCH_TOP_IMPRESSION_SHARE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ABSOLUTE_TOP_IMPRESSION_PERCENTAGE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| SEARCH_RANK_LOST_TOP_IMPRESSION_SHARE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| SEARCH_RANK_LOST_ABSOLUTE_TOP_IMPRESSION_SHARE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| SEARCH_BUDGET_LOST_TOP_IMPRESSION_SHARE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| SEARCH_BUDGET_LOST_ABSOLUTE_TOP_IMPRESSION_SHARE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| LANDING_PAGE_URL | フィールドの名称が変わります。詳細は下記をご確認下さい |
| LANDING_PAGE_URL_SMARTPHONE | フィールドの名称が変わります。詳細は下記をご確認下さい |
| ALL_CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ALL_CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |

DEVICEの変更内容の詳細

| 変更前（日本語表示名称） | 変更前（英語表示名称） | 変更後（日本語表示名称） | 変更後（英語表示名称） |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

LANDING_PAGE_URLの変更内容の詳細

|  | 変更前 | 変更後 |
| --- | --- | --- |
| ENUM | LANDING_PAGE_URL | FINAL_URL |
| 日本語表示名称 | 最終リンク先URL | 最終リンク先URL |
| 英語表示名称 | Landing Page URL | Final URL |

LANDING_PAGE_URL_SMARTPHONEの変更内容の詳細

|  | 変更前 | 変更後 |
| --- | --- | --- |
| ENUM | LANDING_PAGE_URL_SMARTPHONE | FINAL_URL_SMARTPHONE |
| 日本語表示名称 | 最終リンク先URL（スマートフォン） | スマートフォン向けURL |
| 英語表示名称 | Landing Page URL (Smartphone) | Smartphone final URL |

### 組み合わせ不可項目の変更点
2021年9月13日に掲載されるv6のAPIリファレンスをご確認ください。

## 検索クエリーレポート: `SEARCH_QUERY`
### フィールドごとの変更点

| フィールド | 変更内容 |
| --- | --- |
| AVG_DELIVER_RANK | 削除されます |
| SEARCH_QUERY_DESTINATION_URL | 削除されます |
| AVG_CPC | 桁数処理が切り捨てから四捨五入になります |
| COST_PER_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| COST_PER_ALL_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| DEVICE | レポートの値が変わります。詳細は下記をご確認下さい |
| TOP_IMPRESSION_PERCENTAGE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ABSOLUTE_TOP_IMPRESSION_PERCENTAGE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| LANDING_PAGE_URL | フィールドの名称が変わります。詳細は下記をご確認下さい |
| ALL_CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ALL_CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |

DEVICEの変更内容の詳細

| 変更前（日本語表示名称） | 変更前（英語表示名称） | 変更後（日本語表示名称） | 変更後（英語表示名称） |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

LANDING_PAGE_URLの変更内容の詳細

|  | 変更前 | 変更後 |
| --- | --- | --- |
| ENUM | LANDING_PAGE_URL | FINAL_URL |
| 日本語表示名称 | 最終リンク先URL | 最終リンク先URL |
| 英語表示名称 | Landing Page URL | Final URL |

### 組み合わせ不可項目の変更点
2021年9月13日に掲載されるv6のAPIリファレンスをご確認ください。

## 地域別レポート: `GEO`
### フィールドごとの変更点

| フィールド | 変更内容 |
| --- | --- |
| METRO_AREA | 追加されます<br/>フィールド名: METRO_AREA、日本語表示名称: 大都市圏、英語表示名称: Metro Area |
| AVG_CPC | 桁数処理が切り捨てから四捨五入になります |
| COST_PER_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| COST_PER_ALL_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| DEVICE | レポートの値が変わります。詳細は下記をご確認下さい |
| CITY_WARD_DISTRICT | レポートの値が変わります。詳細は下記をご確認下さい |
| ALL_CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ALL_CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |

DEVICEの変更内容の詳細

| 変更前（日本語表示名称） | 変更前（英語表示名称） | 変更後（日本語表示名称） | 変更後（英語表示名称） |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

CITY_WARD_DISTRICTの変更内容の詳細

|  | 変更前 | 変更後 |
| --- | --- | --- |
| フィールド名 | CITY_WARD_DISTRICT | MOST_SPECIFIC_LOCATION |
| 日本語表示名称 | 市・区・郡 | 地域の詳細 |
| 英語表示名称 | City/Ward/District | Location |

### 組み合わせ不可項目の変更点
2021年9月13日に掲載されるv6のAPIリファレンスをご確認ください。

### 全体の変更点
- 出力項目にLOCATION_TYPEを選択されていない場合も、LOCATION_TYPEにて内容が分かれた状態で出力されます。
- CITYの値が「その他」の行が一部表示されなくなります。<br>これにより、アカウントレポートなどと比べ合計に差異が発生します。

## 広告表示オプションレポート: `FEED_ITEM`
データ自動挿入レポートが廃止になり、広告表示オプションレポートにデータ自動挿入レポートのフィールドが追加されます。

### フィールドごとの変更点

| フィールド | 変更内容 |
| --- | --- |
| FEED_ITEM_ATTRIBUTES | 追加されます。詳細はデータ自動挿入レポートのドキュメントをご確認下さい |
| TARGET_LOCATION_NAME | 追加されます。詳細はデータ自動挿入レポートのドキュメントをご確認下さい |
| KEYWORD_TARGETING_TEXT | 追加されます。詳細はデータ自動挿入レポートのドキュメントをご確認下さい |
| KEYWORD_TARGETING_MATCH_TYPE | 追加されます。詳細はデータ自動挿入レポートのドキュメントをご確認下さい |
| TARGETING_CAMPAIGN_ID | 追加されます。詳細はデータ自動挿入レポートのドキュメントをご確認下さい |
| TARGETING_ADGROUP_ID | 追加されます。詳細はデータ自動挿入レポートのドキュメントをご確認下さい |
| TARGET_LOCATION_RESTRICTION | 追加されます。詳細はデータ自動挿入レポートのドキュメントをご確認下さい |
| AVG_DELIVER_RANK | 削除されます |
| AVG_CPC | 桁数処理が切り捨てから四捨五入になります |
| COST_PER_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| COST_PER_ALL_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| DEVICE | レポートの値が変わります。詳細は下記をご確認下さい |
| ATTRIBUTE_VALUES_JSON | 【変更前】 "{""1"":""オプション1"",""2"":[""オプション21"",""オプション22"",""オプション23""]}"<br/>【変更後】 "[{""feedAttributeId"":""1"",""value"":""オプション1""},{""feedAttributeId"":""2"",""values"":[""オプション21"",""オプション22"",""オプション23""]}]" |
| PLACEHOLDER_TYPE | PLACEHOLDER_TYPEの値に「アドカスタマイザー（英語表示名称: Data Auto Insertion）」が追加されます |
| LANDING_PAGE_URL | フィールドの名称が変わります。詳細は下記をご確認下さい |
| LANDING_PAGE_URL_SMARTPHONE | フィールドの名称が変わります。詳細は下記をご確認下さい |
| ALL_CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ALL_CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |

DEVICEの変更内容の詳細

| 変更前（日本語表示名称） | 変更前（英語表示名称） | 変更後（日本語表示名称） | 変更後（英語表示名称） |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

LANDING_PAGE_URLの変更内容の詳細

|  | 変更前 | 変更後 |
| --- | --- | --- |
| ENUM | LANDING_PAGE_URL | FINAL_URL |
| 日本語表示名称 | 最終リンク先URL | 最終リンク先URL |
| 英語表示名称 | Landing Page URL | Final URL |

LANDING_PAGE_URL_SMARTPHONEの変更内容の詳細

|  | 変更前 | 変更後 |
| --- | --- | --- |
| ENUM | LANDING_PAGE_URL_SMARTPHONE | FINAL_URL_SMARTPHONE |
| 日本語表示名称 | 最終リンク先URL（スマートフォン） | スマートフォン向けURL |
| 英語表示名称 | Landing Page URL (Smartphone) | Smartphone final URL |

### 組み合わせ不可項目の変更点
2021年9月13日に掲載されるv6のAPIリファレンスをご確認ください。

## 地域ターゲティングレポート: `GEO_TARGET`

### フィールドごとの変更点

| フィールド | 変更内容 |
| --- | --- |
| AVG_DELIVER_RANK | 削除されます |
| AVG_CPC | 桁数処理が切り捨てから四捨五入になります |
| COST_PER_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| COST_PER_ALL_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| ALL_CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ALL_CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |

### 組み合わせ不可項目の変更点
2021年9月13日に掲載されるv6のAPIリファレンスをご確認ください。

## 曜日・時間帯ターゲティングレポート: `SCHEDULE_TARGET`

### フィールドごとの変更点

| フィールド | 変更内容 |
| --- | --- |
| AVG_DELIVER_RANK | 削除されます |
| AVG_CPC | 桁数処理が切り捨てから四捨五入になります |
| COST_PER_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| COST_PER_ALL_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| ALL_CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ALL_CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |

### 組み合わせ不可項目の変更点
2021年9月13日に掲載されるv6のAPIリファレンスをご確認ください。

## 自動入札レポート: `BID_STRATEGY`

### フィールドごとの変更点

| フィールド | 変更内容 |
| --- | --- |
| AVG_DELIVER_RANK | 削除されます |
| ADGROUP_COUNT | 削除されます |
| AVG_CPC | 桁数処理が切り捨てから四捨五入になります |
| COST_PER_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| COST_PER_ALL_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| ALL_CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ALL_CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| DEVICE | レポートの値が変わります。詳細は下記をご確認下さい |

DEVICEの変更内容の詳細

| 変更前（日本語表示名称） | 変更前（英語表示名称） | 変更後（日本語表示名称） | 変更後（英語表示名称） |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

### 組み合わせ不可項目の変更点
2021年9月13日に掲載されるv6のAPIリファレンスをご確認ください。

## ターゲットリストレポート: `TARGET_LIST`

ターゲットリストレポートは廃止になります。代わりに、キャンペーン単位と広告グループ単位でキャンペーンターゲットリストレポートと広告グループターゲットリストレポートに分割されます。

## キャンペーンターゲットリストレポート: `CAMPAIGN_TARGET_LIST`

### レポートタイプの名称

- レポートタイプ名: CAMPAIGN_TARGET_LIST
- 日本語表示名称: キャンペーンターゲットリストレポート
- 英語表示名称: Campaign Target List Report  

### フィールドごとの変更点

| フィールド | 変更内容 |
| --- | --- |
| AVG_DELIVER_RANK | 削除されます |
| ADGROUP_ID | 削除されます |
| ADGROUP_NAME | 削除されます |
| TARGET_LIST_ATTACHMENT_LEVEL | 削除されます |
| ADGROUP_TRACKING_ID | 削除されます |
| AVG_CPC | 桁数処理が切り捨てから四捨五入になります |
| COST_PER_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| COST_PER_ALL_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| DEVICE | レポートの値が変わります。詳細は下記をご確認下さい |

DEVICEの変更内容の詳細

| 変更前（日本語表示名称） | 変更前（英語表示名称） | 変更後（日本語表示名称） | 変更後（英語表示名称） |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

### 組み合わせ不可項目の変更点
2021年9月13日に掲載されるv6のAPIリファレンスをご確認ください。

## 広告グループターゲットリストレポート: `ADGROUP_TARGET_LIST`

### レポートタイプの名称

- レポートタイプ名: ADGROUP_TARGET_LIST
- 日本語表示名称: 広告グループターゲットリストレポート
- 英語表示名称: Ad Group Target List Report  

### フィールドごとの変更点

| フィールド | 変更内容 |
| --- | --- |
| AVG_DELIVER_RANK | 削除されます |
| TARGET_LIST_ATTACHMENT_LEVEL | 削除されます |
| AVG_CPC | 桁数処理が切り捨てから四捨五入になります |
| COST_PER_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| COST_PER_ALL_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| DEVICE | レポートの値が変わります。詳細は下記をご確認下さい |

DEVICEの変更内容の詳細

| 変更前（日本語表示名称） | 変更前（英語表示名称） | 変更後（日本語表示名称） | 変更後（英語表示名称） |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

### 組み合わせ不可項目の変更点
2021年9月13日に掲載されるv6のAPIリファレンスをご確認ください。

## ページフィードターゲティングレポート: `WEBPAGE_CRITERION`

### フィールドごとの変更点

| フィールド | 変更内容 |
| --- | --- |
| AVG_DELIVER_RANK | 削除されます |
| AVG_CPC | 桁数処理が切り捨てから四捨五入になります |
| COST_PER_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| COST_PER_ALL_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| TOP_IMPRESSION_PERCENTAGE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ABSOLUTE_TOP_IMPRESSION_PERCENTAGE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ALL_CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ALL_CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| DEVICE | レポートの値が変わります。詳細は下記をご確認下さい |

DEVICEの変更内容の詳細

| 変更前（日本語表示名称） | 変更前（英語表示名称） | 変更後（日本語表示名称） | 変更後（英語表示名称） |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

### 組み合わせ不可項目の変更点
2021年9月13日に掲載されるv6のAPIリファレンスをご確認ください。

## 検索クエリーレポート（動的検索連動型広告）: `KEYWORDLESS_QUERY`

### フィールドごとの変更点

| フィールド | 変更内容 |
| --- | --- |
| AVG_DELIVER_RANK | 削除されます |
| DOMAIN | 削除されます |
| QUERY_TARGETING_STATUS | 削除されます |
| AVG_CPC | 桁数処理が切り捨てから四捨五入になります |
| COST_PER_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| COST_PER_ALL_CONV | レポートの値が小数点以下の値なし（桁数処理は切り捨て）から小数点以下の値あり（桁数処理は四捨五入）になります |
| ALL_CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| ALL_CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |
| CONV_VALUE_PER_COST | 桁数処理が小数点第3位で四捨五入から小数点第5位で四捨五入になります |

### レポート行数の変化
行の最小単位がSEARCH_QUERYからSEARCH_QUERY+URLになるため、行数が増える可能性があります。

### 組み合わせ不可項目の変更点
2021年9月13日に掲載されるv6のAPIリファレンスをご確認ください。

## データ自動挿入レポート: `AD_CUSTOMIZERS`

データ自動挿入レポートは廃止になります。代わりに広告表示オプションレポートにデータ自動挿入レポートのフィールドが追加されます。

## 最終リンク先URLレポート: `LANDING_PAGE_URL`

最終リンク先URLレポートは最終リンク先URLのレポートでしたが、v6からはランディングページURLのレポートになります。<br>
それに伴い、レポートタイプの名称とフィールドも変更されます。詳細は下記をご確認ください。

### レポートタイプの名称

- レポートタイプ名: LANDING_PAGE_URL
- 日本語表示名称: ランディングページURLレポート
- 英語表示名称: Landing Page URL Report  

### フィールド

#### フィールド一覧

| フィールド |
| --- |
| IMPS |
| CLICKS |
| CLICK_RATE |	
| AVG_CPC |	
| LANDING_PAGE_URL |
| EXPANDED_LANDING_PAGE_URL |
| CONVERSION |
| CONV_RATE	 |
| CONV_VALUE |	
| COST_PER_CONV |	
| VALUE_PER_CONV	 |
| ALL_CONV	 |
| ALL_CONV_RATE |	
| ALL_CONV_VALUE	 |
| COST_PER_ALL_CONV	 |
| VALUE_PER_ALL_CONV |	
| CROSS_DEVICE_CONVERSIONS |	
| CAMPAIGN_TRACKING_ID	 |
| ADGROUP_TRACKING_ID	 |
| NETWORK	 |
| DEVICE	 |
| DAY	 |
| DAY_OF_WEEK |	
| QUARTER	 |
| YEAR	 |
| MONTH	 |
| MONTH_OF_YEAR |	
| WEEK |	
| OBJECT_OF_CONVERSION_TRACKING |	
| CONVERSION_NAME |	
| CONV_VALUE_PER_COST |	
| ALL_CONV_VALUE_PER_COST |
	
#### 新規フィールドの詳細

ランディングページURLレポートで新しく追加されるフィールドは下記の通りです。

| ENUM | LANDING_PAGE_URL |
| --- | --- |
| 和名 | ランディングページURL |
| 英名 | Landing Page URL |
| 説明 | URLパラメータが非展開のランディングページURL（広告がクリックされていない場合は最終リンク先URL） |


| ENUM | EXPANDED_LANDING_PAGE_URL |
| --- | --- |
| 和名 | ランディングページURL（詳細） |
| 英名 | Expanded Landing Page URL |
| 説明 | URLパラメータが展開されたランディングページURL（広告がクリックされていない場合は最終リンク先URL） |

### 組み合わせ不可項目
2021年9月13日に掲載されるv6のAPIリファレンスをご確認ください。

### その他
includeDeletedは設定できません

## 入札価格調整率レポート: `BID_MODIFIER`

キャンペーンレポートと広告グループレポートの入札価格調整率系のフィールドが廃止になり、代わりに入札価格調整率を取得するためのレポートタイプを提供します。

### レポートタイプの名称

- レポートタイプ名: BID_MODIFIER
- 日本語表示名称: 入札価格調整率レポート
- 英語表示名称: Bid Adjustments Report  

### フィールド

#### フィールド一覧

| フィールド | 備考 |
| --- | ---|
| ACCOUNT_ID	 | |
| ACCOUNT_NAME | |
| ADGROUP_ID	 | |
| ADGROUP_NAME	 | |
| CAMPAIGN_ID | |
| CAMPAIGN_NAME | |
| DEVICE_TYPE	 | |
| BID_MULTIPLIER	 | レポートの値は小数点以下の値あり（桁数処理は切り捨て）になります。 |
| BID_MODIFIER_ATTACHMENT_LEVEL | |

#### 新規フィールドの詳細

| ENUM | DEVICE_TYPE |
| --- | --- |
| 和名 | 入札価格調整率を設定したデバイス |
| 英名 | Device |
| 説明 | 入札価格調整率を設定したデバイス |

| ENUM | BID_MODIFIER_ATTACHMENT_LEVEL |
| --- | --- |
| 和名 | 入札価格調整率の対象 |
| 英名 | Level |
| 説明 | 入札価格調整率を設定した階層（キャンペーン、広告グループ） |

### 組み合わせ不可項目
2021年9月13日に掲載されるv6のAPIリファレンスをご確認ください。

### その他
- 期間設定は必須ではありません
- include0imps、includeDeletedは設定できません

