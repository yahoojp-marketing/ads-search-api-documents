# Changes on each report type

Yahoo! JAPAN Search Ads API v6 changes the following output items (fields) by each report type on ReportDefinitionService.

## Index

- [Account Report: `ACCOUNT`](#account-report-account)
- [Campaign Report: `CAMPAIGN`](#campaign-report-campaign)
- [Ad Group Report: `ADGROUP`](#ad-group-report-adgroup)
- [Ad Report: `AD`](#ad-report-ad)
- [Keyword Report: `KEYWORDS`](#keyword-report-keywords)
- [Search Query Report: `SEARCH_QUERY`](#search-query-report-search_query)
- [Geo Report: `GEO`](#geo-report-geo)
- [Ad Display Option Report: `FEED_ITEM`](#ad-display-option-report-feed_item)
- [Geo Targeting Report: `GEO_TARGET`](#geo-targeting-report-geo_target)
- [Schedule Targeting Report: `SCHEDULE_TARGET`](#schedule-targeting-report-schedule_target)
- [Auto Bidding Report `BID_STRATEGY`](#auto-bidding-report-bid_strategy)
- [Target List Setting Report: `TARGET_LIST`](#target-list-setting-report-target_list)
- [Campaign Target List Report: `CAMPAIGN_TARGET_LIST`](#campaign-target-list-report-campaign_target_list)
- [Ad Group Target List Report: `ADGROUP_TARGET_LIST`](#ad-group-target-list-report-adgroup_target_list)
- [Search Query Report (DAS): `KEYWORDLESS_QUERY`](#search-query-report-dynamic-ads-for-search-keywordless_query)
- [Data Auto Insertion Report: `AD_CUSTOMIZERS`](#data-auto-insertion-report-ad_customizers)
- [Page Feed Targeting Report: `WEBPAGE_CRITERION`](#page-feed-targeting-report-webpage_criterion)
- [Landing Page URL Report: `LANDING_PAGE_URL`](#landing-page-url-report-landing_page_url)
- [Bid Adjustment Report: `BID_MODIFIER`](#bid-adjustments-report-bid_modifier)


## Account Report `ACCOUNT`

| Field | Changes |
| --- | --- |
| AVG_DELIVER_RANK | To be deleted |
| EXACT_MATCH_IMPRESSION_SHARE | If the value is less than 0.1, the value in the report will change from 0.1 to 0.0999.<br/>If the value is more than 0.9, the value in the report will change from 0.9 to 0.9001. |
| IMPRESSION_SHARE | If the value is less than 0.1, the value in the report will change from 0.1 to 0.0999. |
| BUDGET_LOST_IMPRESSION_SHARE | If the value is more than 0.9, the value in the report will change from 0.9 to 0.9001. |
| QUALITY_LOST_IMPRESSION_SHARE | If the value is more than 0.9, the value in the report will change from 0.9 to 0.9001. |
| AVG_CPC | Digit processing will change from rounding down to being rounded. |
| COST_PER_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| COST_PER_ALL_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| DEVICE | The value in the report changes. See the following details |

Changes on DEVICE

| Before (Japanese) | Before (English) | After (Japanese) | After (English) |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

### Changes on items that cannot be combined
Check out the v6 API reference that will be posted on September 13, 2021.

## Campaign Report: `CAMPAIGN`
### Changes by each field

| Field | Change |
| --- | --- |
| AVG_DELIVER_RANK | To be deleted |
| CAMPAIGN_MOBILE_BID_MODIFIER | Deleted Use Bid Adjustment Report. |
| CAMPAIGN_DESKTOP_BID_MODIFIER | Deleted Use Bid Adjustment Report. |
| CAMPAIGN_TABLET_BID_MODIFIER | Deleted Use Bid Adjustment Report. |
| EXACT_MATCH_IMPRESSION_SHARE | If the value is less than 0.1, the value in the report will change from 0.1 to 0.0999.<br/>If the value is more than 0.9, the value in the report will change from 0.9 to 0.9001. |
| IMPRESSION_SHARE | If the value is less than 0.1, the value in the report will change from 0.1 to 0.0999. |
| SEARCH_ABSOLUTE_TOP_IMPRESSION_SHARE | If the value is less than 0.1, the value in the report will change from 0.1 to 0.0999. |
| SEARCH_BUDGET_LOST_ABSOLUTE_TOP_IMPRESSION_SHARE | If the value is less than 0.1, the value in the report will change from 0.1 to 0.0999. |
| SEARCH_BUDGET_LOST_TOP_IMPRESSION_SHARE | If the value is less than 0.1, the value in the report will change from 0.1 to 0.0999. |
| BUDGET_LOST_IMPRESSION_SHARE | If the value is more than 0.9, the value in the report will change from 0.9 to 0.9001. |
| QUALITY_LOST_IMPRESSION_SHARE | If the value is more than 0.9, the value in the report will change from 0.9 to 0.9001. |
| EXACT_MATCH_IMPRESSION_SHARE | If the value is more than 0.9, the value in the report will change from 0.9 to 0.9001. |
| AVG_CPC | Digit processing will change from rounding down to being rounded. |
| COST_PER_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| COST_PER_ALL_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| DEVICE | The value in the report changes. See the following details |
| LABELS_JSON | [Before]"[""Label 1"",""Label 2""]" <br/>[After]"[{""labelId"":""1"",""value"":""Label 1""},{""labelId"":""2"",""value"":""Label 2""}]" |
| TOP_IMPRESSION_PERCENTAGE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| SEARCH_TOP_IMPRESSION_SHARE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| ABSOLUTE_TOP_IMPRESSION_PERCENTAGE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| SEARCH_RANK_LOST_TOP_IMPRESSION_SHARE |Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| SEARCH_RANK_LOST_ABSOLUTE_TOP_IMPRESSION_SHARE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| SEARCH_BUDGET_LOST_TOP_IMPRESSION_SHARE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place.|
| SEARCH_BUDGET_LOST_ABSOLUTE_TOP_IMPRESSION_SHARE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place.

Change details on DEVICE

| Before (Japanese) | Before (English) | After (Japanese) | After (English) |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

### Changes on items that cannot be combined
Check out the v6 API reference that will be posted on September 13, 2021.

## Ad Group Report: `ADGROUP`
### Changes by each field

| Field | Change |
| --- | --- |
| AVG_DELIVER_RANK | To be deleted Use Bid Adjustment Report. |
| ADGROUP_DESKTOP_BID_MODIFIER | Deleted Use Bid Adjustment Report. |
| ADGROUP_TABLET_BID_MODIFIER | Deleted Use Bid Adjustment Report. |
| EXACT_MATCH_IMPRESSION_SHARE | If the value is less than 0.1, the value in the report will change from 0.1 to 0.0999.<br/>If the value is more than 0.9, the value in the report will change from 0.9 to 0.9001. |
| IMPRESSION_SHARE | If the value is less than 0.1, the value in the report will change from 0.1 to 0.0999. |
| SEARCH_ABSOLUTE_TOP_IMPRESSION_SHARE | If the value is less than 0.1, the value in the report will change from 0.1 to 0.0999. |
| SEARCH_BUDGET_LOST_ABSOLUTE_TOP_IMPRESSION_SHARE | If the value is less than 0.1, the value in the report will change from 0.1 to 0.0999. |
| SEARCH_BUDGET_LOST_TOP_IMPRESSION_SHARE | If the value is less than 0.1, the value in the report will change from 0.1 to 0.0999. |
| BUDGET_LOST_IMPRESSION_SHARE | If the value is more than 0.9, the value in the report will change from 0.9 to 0.9001. |
| QUALITY_LOST_IMPRESSION_SHARE | If the value is more than 0.9, the value in the report will change from 0.9 to 0.9001. |
| EXACT_MATCH_IMPRESSION_SHARE | If the value is more than 0.9, the value in the report will change from 0.9 to 0.9001. |
| AVG_CPC | Digit processing will change from rounding down to being rounded. |
| COST_PER_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| COST_PER_ALL_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). | 
| DEVICE | The value in the report changes. See the following details |
| LABELS_JSON | [Before]"[""Label 1"",""Label 2""]" <br/>[After]"[{""labelId"":""1"",""value"":""Label 1""},{""labelId"":""2"",""value"":""Label 2""}]" |
| TOP_IMPRESSION_PERCENTAGE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| SEARCH_TOP_IMPRESSION_SHARE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place.|
| ABSOLUTE_TOP_IMPRESSION_PERCENTAGE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| SEARCH_RANK_LOST_TOP_IMPRESSION_SHARE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| SEARCH_RANK_LOST_ABSOLUTE_TOP_IMPRESSION_SHARE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| SEARCH_BUDGET_LOST_TOP_IMPRESSION_SHARE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| SEARCH_BUDGET_LOST_ABSOLUTE_TOP_IMPRESSION_SHARE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place.

Change details on DEVICE

| Before (Japanese) | Before (English) | Before (Japanese) | After (English) |
| --- | --- | --- | --- |
|| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

### Changes on items that cannot be combined
Check out the v6 API reference that will be posted on September 13, 2021.

## Ad Report: `AD`
### Changes by each field

| Field | Change |
| --- | --- |
| AVG_DELIVER_RANK | Deleted |
| TITLE | To be deleted |
| DESC | To be deleted |
| DESCRIPTION | Deleted |
| AVG_CPC | Digit processing will change from rounding down to being rounded. |
| COST_PER_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| COST_PER_ALL_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| DEVICE | The value in the report changes. See the following details |
| LABELS_JSON | [Before]"[""Label 1"",""Label 2""]" <br/>[After]"[{""labelId"":""1"",""value"":""Label 1""},{""labelId"":""2"",""value"":""Label 2""}]" |
| TOP_IMPRESSION_PERCENTAGE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| ABSOLUTE_TOP_IMPRESSION_PERCENTAGE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| LANDING_PAGE_URL | The field name changes. See the following details |
| LANDING_PAGE_URL_SMARTPHONE | The field name changes. See the following details |

Change details on DEVICE

| Before (Japanese) | Before (English) | After (Japanese) | After (English) |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

Change details on LANDING_PAGE_URL

|  | Before | After |
| --- | --- | --- |
| ENUM | LANDING_PAGE_URL | FINAL_URL |
| Japanese | 最終リンク先URL | 最終リンク先URL |
| English | Landing Page URL | Final URL |

Change details on LANDING_PAGE_URL_SMARTPHONE

|  | Before | After |
| --- | --- | --- |
| ENUM | LANDING_PAGE_URL_SMARTPHONE | FINAL_URL_SMARTPHONE |
| Japanese | 最終リンク先URL（スマートフォン） | スマートフォン向けURL |
| English | Landing Page URL (Smartphone) | Smartphone final URL |

### Changes on items that cannot be combined
Check out the v6 API reference that will be posted on September 13, 2021.

## Keyword Report: `KEYWORDS`
### Changes by each field

| Field | Change |
| --- | --- |
| AVG_DELIVER_RANK | To be deleted |
| EXACT_MATCH_IMPRESSION_SHARE | If the value is less than 0.1, the value in the report will change from 0.1 to 0.0999.<br/>If the value is more than 0.9, the value in the report will change from 0.9 to 0.9001. |
| IMPRESSION_SHARE | If the value is less than 0.1, the value in the report will change from 0.1 to 0.0999. |
| SEARCH_ABSOLUTE_TOP_IMPRESSION_SHARE | If the value is less than 0.1, the value in the report will change from 0.1 to 0.0999. |
| SEARCH_BUDGET_LOST_ABSOLUTE_TOP_IMPRESSION_SHARE | If the value is less than 0.1, the value in the report will change from 0.1 to 0.0999.|
| SEARCH_BUDGET_LOST_TOP_IMPRESSION_SHARE | If the value is less than 0.1, the value in the report will change from 0.1 to 0.0999. |
| QUALITY_LOST_IMPRESSION_SHARE | If the value is more than 0.9, the value in the report will change from 0.9 to 0.9001. |
| AVG_CPC | Digit processing will change from rounding down to being rounded. |
| COST_PER_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| COST_PER_ALL_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| DEVICE | The value in the report changes. See the following details |
| LABELS_JSON | [Before]"[""Label 1"",""Label 2""]" <br/>[After]"[{""labelId"":""1"",""value"":""Label 1""},{""labelId"":""2"",""value"":""Label 2""}]" |
| TOP_IMPRESSION_PERCENTAGE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place.|
| SEARCH_TOP_IMPRESSION_SHARE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place.|
| ABSOLUTE_TOP_IMPRESSION_PERCENTAGE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| SEARCH_RANK_LOST_TOP_IMPRESSION_SHARE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| SEARCH_RANK_LOST_ABSOLUTE_TOP_IMPRESSION_SHARE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| SEARCH_BUDGET_LOST_TOP_IMPRESSION_SHARE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| SEARCH_BUDGET_LOST_ABSOLUTE_TOP_IMPRESSION_SHARE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| LANDING_PAGE_URL | The field name changes. See the following details |
| LANDING_PAGE_URL_SMARTPHONE | The field name changes. See the following details |

Change details on DEVICE

| Before (Japanese) | Before (English) | After (Japanese) | After (English) |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

Change details on LANDING_PAGE_URL

|  | Before | After |
| --- | --- | --- |
| ENUM | LANDING_PAGE_URL | FINAL_URL |
| Japanese | 最終リンク先URL | 最終リンク先URL |
| English | Landing Page URL | Final URL |

Change details on LANDING_PAGE_URL_SMARTPHONE

|  | Before | After |
| --- | --- | --- |
| ENUM | LANDING_PAGE_URL_SMARTPHONE | FINAL_URL_SMARTPHONE |
| Japanese | 最終リンク先URL（スマートフォン） | スマートフォン向けURL |
| English | Landing Page URL (Smartphone) | Smartphone final URL |

### Changes on items that cannot be combined
Check out the v6 API reference that will be posted on September 13, 2021.

## Search Query Report: `SEARCH_QUERY`
### Changes by each field

| Field | Change |
| --- | --- |
| AVG_DELIVER_RANK | To be deleted |
| SEARCH_QUERY_DESTINATION_URL | To be deleted |
| AVG_CPC | Digit processing will change from rounding down to being rounded. |
| COST_PER_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| COST_PER_ALL_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| DEVICE | The value in the report changes. See the following details |
| TOP_IMPRESSION_PERCENTAGE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| ABSOLUTE_TOP_IMPRESSION_PERCENTAGE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| LANDING_PAGE_URL | The field name changes. See the following details |

Change details on DEVICE

| Before (Japanese)| Before (English) | After (Japanese) | After (English) |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

Change details on LANDING_PAGE_URL

|  | Before | After |
| --- | --- | --- |
| ENUM | LANDING_PAGE_URL | FINAL_URL |
| Japanese | 最終リンク先URL | 最終リンク先URL |
| English | Landing Page URL | Final URL |

### Changes on items that cannot be combined
Check out the v6 API reference that will be posted on September 13, 2021.

### Overall changes
- TRACKING_URL and LANDING_PAGE_URL behave as segments

## Geo Report `GEO`
### Changes by each field

| Field | Change |
| --- | --- |
| METRO_AREA | To be added<br/>Field name: METRO_AREA, Japanese: 大都市圏, English: Metro Area |
| AVG_CPC | Digit processing will change from rounding down to being rounded. |
| COST_PER_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| COST_PER_ALL_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| DEVICE |  See the following details |
| CITY_WARD_DISTRICT | The value in the report changes. See the following details |

Change details on DEVICE

| Before (Japanese) | Before (English) | After (Japanese) | After (English) |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

Change details on CITY_WARD_DISTRICT

| | Before | After |
| --- | --- | --- |
| Field name | CITY_WARD_DISTRICT | MOST_SPECIFIC_LOCATION |
| Japanese |  市・区・郡 | 地域の詳細 |
| English | City/Ward/District | Location |

### Changes on items that cannot be combined
Check out the v6 API reference that will be posted on September 13, 2021.

### Overall changes
- The smallest unit of a row changes from COUNTRY_TERRITORY to COUNTRY_TERRITORY and LOCATION_TYPE
- Rows that do not have a CITY value disappear

## Ad Display Option Report: `FEED_ITEM`
Data Auto Insertion Report is deprecated. Fields of the report are added to Ad Display Option Report.

### Changes by each field

| Field | Change |
| --- | --- |
| FEED_ITEM_ATTRIBUTES | To be added See the details on the document for Data Auto Insertion Report. |
| TARGET_LOCATION_NAME | To be added See the details on the document for Data Auto Insertion Report. |
| KEYWORD_TARGETING_TEXT | To be added See the details on the document for Data Auto Insertion Report. |
| KEYWORD_TARGETING_MATCH_TYPE | To be added See the details on the document for Data Auto Insertion Report. |
| TARGETING_CAMPAIGN_ID | To be added See the details on the document for Data Auto Insertion Report. |
| TARGETING_ADGROUP_ID | To be added See the details on the document for Data Auto Insertion Report. |
| TARGET_LOCATION_RESTRICTION | To be added See the details on the document for Data Auto Insertion Report. |
| AVG_DELIVER_RANK | To be deleted |
| AVG_CPC | Digit processing will change from rounding down to being rounded. |
| COST_PER_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| COST_PER_ALL_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| DEVICE | The value in the report changes. See the following details |
| ATTRIBUTE_VALUES_JSON | [Before] "{""1"":""Option 1"",""2"":[""Option 21"",""Option 22"",""Option 23""]}"<br/>[After] "[{""feedAttributeId"":""1"",""value"":""Option 1""},{""feedAttributeId"":""2"",""values"":[""Option 21"",""Option 22"",""Option 23""]}]" |
| PLACEHOLDER_TYPE | "アドカスタマイザー (Data Auto Insertion)" is added to the value of PLAECEHOLDER_TYPE |
| LANDING_PAGE_URL | The field name changes. See the following details |
| LANDING_PAGE_URL_SMARTPHONE | The field name changes. See the following details |

Change details on DEVICE

| Before (Japanese) | Before (English) | After (Japanese) | After (English) |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

Change details on LANDING_PAGE_URL

| | Before | After |
| --- | --- | --- |
| ENUM | LANDING_PAGE_URL | FINAL_URL |
| Japanese | 最終リンク先URL | 最終リンク先URL |
| English | Landing Page URL | Final URL |

Change details on LANDING_PAGE_URL_SMARTPHONE

| | Before | After |
| --- | --- | --- |
| ENUM | LANDING_PAGE_URL_SMARTPHONE | FINAL_URL_SMARTPHONE |
| Japanese | 最終リンク先URL（スマートフォン） | スマートフォン向けURL |
| English | Landing Page URL (Smartphone) | Smartphone final URL |

### Changes on items that cannot be combined
Check out the v6 API reference that will be posted on September 13, 2021.

## Geo Targeting Report `GEO_TARGET`

### Changes by each field

| Field | Change |
| --- | --- |
| AVG_DELIVER_RANK | To be deleted |
| AVG_CPC | Digit processing will change from rounding down to being rounded. |
| COST_PER_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| COST_PER_ALL_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number).

### Changes on items that cannot be combined
Check out the v6 API reference that will be posted on September 13, 2021.

## Schedule Targeting Report `SCHEDULE_TARGET`

### Changes by each field

| Field | Change |
| --- | --- |
| AVG_DELIVER_RANK | To be deletedDigit processing will change from rounding down to being rounded. |
| COST_PER_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| COST_PER_ALL_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |

### Changes on items that cannot be combined
Check out the v6 API reference that will be posted on September 13, 2021.

## Auto Bidding Report `BID_STRATEGY`

### Changes by each field

| Field | Change |
| --- | --- |
| AVG_DELIVER_RANK | To be deleted |
| ADGROUP_COUNT | To be deleted | 
 AVG_CPC | Digit processing will change from rounding down to being rounded. |
| COST_PER_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| COST_PER_ALL_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| DEVICE |  See the following details |

Change details on DEVICE

| Before (Japanese) | Before (English) | After (Japanese) | After (English) |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

### Changes on items that cannot be combined
Check out the v6 API reference that will be posted on September 13, 2021.

## Target List Setting Report: `TARGET_LIST`

Target List Report is deprecated. It is separated to Campaign Target List Report by each campaign and Ad Group Target List Report by each ad group instead.

## Campaign Target List Report: `CAMPAIGN_TARGET_LIST`

### Name of report type

- Report type name: CAMPAIGN_TARGET_LIST
- Japanese: キャンペーンターゲットリストレポート
- English: Campaign Target List Report  

### Changes by each field

| Field | Change |
| --- | --- |
| AVG_DELIVER_RANK | To be deleted |
| ADGROUP_ID | To be deleted |
| ADGROUP_NAME | To be deleted |
| TARGET_LIST_ATTACHMENT_LEVEL | To be deleted |
| ADGROUP_TRACKING_ID | To be deleted |
| AVG_CPC | Digit processing will change from rounding down to being rounded. |
| COST_PER_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| COST_PER_ALL_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| DEVICE | The value in the report changes. See the following details |

Change details on DEVICE

| Before (Japanese) | Before (English) | After (Japanese) | After (English) |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

### Changes on items that cannot be combined
Check out the v6 API reference that will be posted on September 13, 2021.

## Ad Group Target List Report: `ADGROUP_TARGET_LIST`

### Name of report type

- Report type name: ADGROUP_TARGET_LIST
- Japanese: 広告グループターゲットリストレポート
- English: Ad Group Target List Report  

### Changes by each field

| Field | Change |
| --- | --- |
| AVG_DELIVER_RANK | To be deleted |
| TARGET_LIST_ATTACHMENT_LEVEL | To be deleted |
| AVG_CPC | Digit processing will change from rounding down to being rounded. |
| COST_PER_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| COST_PER_ALL_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| DEVICE | The value in the report changes. See the following details |

Change details on DEVICE

| Before (Japanese) | Before (English) | After (Japanese) | After (English) |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

### Changes on items that cannot be combined
Check out the v6 API reference that will be posted on September 13, 2021.

## Page Feed Targeting Report: `WEBPAGE_CRITERION`

### Changes by each field

| Field | Changes |
| --- | --- |
| AVG_DELIVER_RANK | To be deleted |
| AVG_CPC | Digit processing will change from rounding down to being rounded. |
| COST_PER_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| COST_PER_ALL_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| TOP_IMPRESSION_PERCENTAGE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| ABSOLUTE_TOP_IMPRESSION_PERCENTAGE | Digit processing will change from being rounded from the 3rd decimal place to the 5th decimal place. |
| DEVICE | The value in the report changes. See the following details |

Change details on DEVICE

| Before (Japanese) | Before (English) | After (Japanese) | After (English) |
| --- | --- | --- | --- |
| PC | Computers | PC | PC |
| フルブラウザ搭載の携帯端末 | Mobile devices with full browsers | スマートフォン | Smartphone |
| フルブラウザ搭載のタブレット端末 | Tablets with full browsers | タブレット | Tablet |

### Changes on items that cannot be combined
Check out the v6 API reference that will be posted on September 13, 2021.

## Search Query Report (Dynamic Ads for Search): `KEYWORDLESS_QUERY`

### Changes by each field

| Field | Changes |
| --- | --- |
| AVG_DELIVER_RANK | To be deleted |
| DOMAIN | To be deleted |
| QUERY_TARGETING_STATUS | To be deleted |
| AVG_CPC | Digit processing will change from rounding down to being rounded. |
| COST_PER_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |
| COST_PER_ALL_CONV | The value in the report changes from no decimal point value (rounded down to the nearest whole number) to a value after the decimal point (rounded down to the nearest whole number). |

### Changes on items that cannot be combined
Check out the v6 API reference that will be posted on September 13, 2021.

## Data Auto Insertion Report: `AD_CUSTOMIZERS`

Data Auto Insertion Report is deprecated. Fields of Data Auto Insertion Report are added to Ad Display Option Report instead.

## Landing Page URL Report: `LANDING_PAGE_URL`

Landing Page URL Report becomes the report of Landing Page URL on v6.<br>
The report type names and fields will change accordingly. See the following details.

### Name of report type

- Report type name: LANDING_PAGE_URL
- Japanese: ランディングページURLレポート
- English: Landing Page URL Report  

### Field

#### Field list

| Field |
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
	
#### New fields detail

Following new fields are added to Landing page URL report.

| ENUM | LANDING_PAGE_URL |
| --- | --- |
| Japanese | ランディングページURL |
| English | Landing Page URL |
| Description | Landing page URL with unexpanded URL parameters (If no click on ad, Landing Page URL) |


| ENUM | EXPANDED_LANDING_PAGE_URL |
| --- | --- |
| Japanese | ランディングページURL（詳細） |
| English | Expanded Landing Page URL |
| Description | Landing page URL with expanded URL parameters (If no click on ad, Landing Page URL) |

### Changes on items that cannot be combined
Check out the v6 API reference that will be posted on September 13, 2021.

### Other
includeDeleted is not available for setting.

## Bid Adjustments Report: `BID_MODIFIER`

The bid adjustment fields in Campaign Report and Ad Group Report are deprecated and a report type for getting Bid Adjustment rate is provided instead.

### Name of report type

- Report type name: BID_MODIFIER
- Japanese: 入札価格調整率レポート
- English: Bid Adjustments Report  

### Field

#### Field list

| Field |
| --- |
| ACCOUNT_ID	 |
| ACCOUNT_NAME |
| ADGROUP_ID	 |
| ADGROUP_NAME	 |
| CAMPAIGN_ID |
| CAMPAIGN_NAME |
| DEVICE_TYPE	 |
| BID_MULTIPLIER	 |
| BID_MODIFIER_ATTACHMENT_LEVEL |

#### New fields detail

| ENUM | DEVICE_TYPE |
| --- | --- |
| Japanese | 入札価格調整率を設定したデバイス |
| English | Device |
| Description | Device that has Bid adjustment setting |

| ENUM | BID_MODIFIER_ATTACHMENT_LEVEL |
| --- | --- |
| Japanese | 入札価格調整率の対象 |
| English | Level |
| Description | Component layer (Campaign, Ad group) that has Bid adjustment setting |

### Changes on items that cannot be combined
Check out the v6 API reference that will be posted on September 13, 2021.

### Other
- Duration setting is optional.
- include0imps and includeDeleted are not available for setting.

