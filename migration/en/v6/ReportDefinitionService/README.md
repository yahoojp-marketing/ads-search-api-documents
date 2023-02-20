# ReportDefinitionService v6 Migration Guide

There are changes on some report output items on ReportDefinitionService of Yahoo! JAPAN Ads Search Ads API v6.<br>
This document describes the required actions on the migration from v5 ReportDefinitionService to v6 ReportDefinitionService.

## Index

- [Changes](#Changes)
  - [ReportDefinitionService/add](#reportdefinitionserviceadd)
  - [ReportDefinitionService/download](#reportdefinitionservicedownload)
- [Q&A](#qa)
  - [What are the changes on report output items? ](#what-are-the-detailed-changes-in-the-report-output-items)
  - [Is there any change on QPS?](#is-there-any-change-on-qps)
  - [Is there any other change on v6?](#is-there-any-other-change-on-v6)

## Changes

v6 ReportDefinitionService has changes on some report types and report output items (fields).

### ReportDefinitionService/add

#### Change details

- Report output item (field) change
  - **Refer to [Changes by Report Type](ReportType.md) for more detail**
- Following report types will deprecate on v6 and later
  - `TARGET_LIST`
  - `AD_CUSTOMIZERS`
  - Refer to [Changes by Report Type](ReportType.md) for the alternative report types
- The reportIncludeZeroImpressions field will be removed in v6 and later versions.
  - In previous versions, by default, items with all zero achievements were excluded.
  - In v6 and later versions, items without achievements are also output together, resulting in a large amount of data and an error may occur when retrieving the report.
  - To output only the items with achievements in the v6 or later version to the report, set the items such as IMPS to 1 or more in the filter condition.
```r
#request sample
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

#### Change details

- Output format change
  - Zero padding abolished on the field type DOUBLE such as `CLICK_RATE`.**`1.0000` → `1`**
  - Display up to 4 decimal places in a field of type DOUBLE such as `CLICK_RATE` (up to 16 digits can be displayed by changing the default setting)
  - A field that contains division when specifying a filter will calculate the total row if its denominator and numerator are specified in the field, but if the denominator and numerator are not included in the field, the total row will be 0.
  - The notation when the value does not exist is changed as follows.

    | | LONG | DOUBLE | STRING ※ | ENUM |
    | --- | --- | --- | --- | --- | 
    | Before | 0 or -- | 0 or -- | -- | --　(or default value) |
    | After | 0 | 0 | "" | "" |

    (※ For ACCOUNT\_ID and ACCOUNT\_NAME, the account ID and account name are entered, they are not "-" or "" ".)

For detailed differences by report type including the preceding changes, refer to [Changes by Report Type](ReportType.md)

#### Sample response

Describing the sample request to /ReportDefinitionService/download of v5 and v6.

```r
#v5 report sample
Account Name,Impressions,Avg.CPC,Conversions across devices,Tracking URL
SampleName,159116,85.4555,--,http://www.example.com
SampleName,43,12.6000,--,--
SampleName,159159,85.5434,--,--
```

```r
#v6 report sample
Account Name,Impressions,Avg.CPC,Conversions across devices,Tracking URL
SampleName,159116,85.4555,0,http://www.example.com
SampleName,43,12.6,0,
SampleName,159159,85.5434,0, 
```

## Q&A

### What are the detailed changes in the report output items?

Refer to [Changes by Report Type](ReportType.md).

### Is there any change on QPS?

No change on QPS.
Refer to the details on [QPS](https://ads-developers.yahoo.co.jp/en/ads-api/developers-guide/qps.html).

### Is there any other change on v6?

The display format for header lines, total lines, and decimal items are selectable when creating a report.
The header row can be specified in the `reportSkipColumnHeader` field, the total row can be specified in the reportSkipReportSummary` field, and the decimal item can be specified in the `reportDecimalPartDisplayType` field.
If not specified, the behavior will be the same as the previous version.

Refer to [API Reference of v6 ReportDefinitionService/add](https://ads-developers.yahoo.co.jp/reference/ads-search-api/v6/ReportDefinitionService/add/) for more detail.
