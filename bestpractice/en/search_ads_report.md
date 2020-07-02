# Creating/Retrieving Search Ad Report
## What is “Performance Report”?
Performance Report is a function of confirming performance in Campaign, Ad Group, Ad, Keyword, etc.   
Customizing report is possible, like setting hierarchy of performance, item display, summary period, etc.  
  
Report functions supported in Campaign Management Tool are also available from API.  

## How to operate from Search Ad API
To display the performance report, use the service below from Search Ad API.  

##### ReportDefinitionService   
ReportDefinitionService can retrieve and add/download the report definition.    

## Scenerio Sample
This is a process of create and download of actual report, to retrieve Performance Report, 
using Search Ad API.  

#### 1. Retrieve Field of Report
Use getReportFields of ReportDefinitionService.  
Retrieve list of available report fields by designated ReportType.  
Each report fields encapsulate the field name, field data type, and enumerations.

##### Request Sample
```json
{
  "reportType": "LANDING_PAGE_URL"
}
```

##### Response Sample
I omit a part.
```json
{
    "errors": null,
    "rid": "11111111",
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

#### 2.	Create Report 
Use add of ReportDefinitionService.  
Creates the report template.
It requires the following:  
* Name of report 
* Designating summary period
* Japanese/English selection
* Designating output format

##### Request Sample
```json
{
  "accountId": "11111111",
  "operand": [
    {
      "dateRange": {
        "endDate": "20371231",
        "startDate": "19700101"
      },
      "fields": [
        "COST",
        "IMPS",
        "CLICKS",
        "CLICK_RATE",
        "AVG_CPC",
        "AVG_DELIVER_RANK",
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
        "MONTH_OF_YEAR",
        "WEEK",
        "HOUR_OF_DAY"
      ],
      "filters": [
        {
          "field": "COST",
          "reportOperator": "NOT_EQUALS",
          "value": [
            "100"
          ]
        }
      ],
      "reportCompressType": "ZIP",
      "reportDateRangeType": "CUSTOM_DATE",
      "reportDownloadEncode": "UTF-8",
      "reportDownloadFormat": "CSV",
      "reportIncludeDeleted": "TRUE",
      "reportIncludeZeroImpressions": "TRUE",
      "reportLanguage": "EN",
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

##### Response Sample
I omit a part.
```json
{
    "errors": null,
    "rid": "11111111",
    "rval": {
        "values": [
            {
                "errors": null,
                "operationSucceeded": true,
                "reportDefinition": {
                    "accountId": 11111111,
                    "completeTime": null,
                    "dateRange": {
                        "endDate": "20371231",
                        "startDate": "19700101"
                    },
                    "fields": [
                        "COST",
                        ...
                    ],
                    "filters": [
                        {
                            "field": "COST",
                            "reportOperator": "NOT_EQUALS",
                            "value": [
                                "100"
                            ]
                        }
                    ],
                    "reportCompressType": "ZIP",
                    "reportDateRangeType": "CUSTOM_DATE",
                    "reportDownloadEncode": "UTF-8",
                    "reportDownloadFormat": "CSV",
                    "reportIncludeDeleted": "TRUE",
                    "reportIncludeZeroImpressions": "TRUE",
                    "reportJobErrorDetail": null,
                    "reportJobId": 11111111,
                    ...
                }
            }
        ]
    }
}
```

#### 3. Confirm the Report Status
Use get of ReportDefinitionService.  
Can confirm the report creation status. <br>
Also, when jobStatus of response is "completed", go to 4.

##### Request Sample
```json
{
  "accountId": 11111111,
  "numberResults": 1,
  "reportJobIds": [
    11111111
  ],
  "startIndex": 1
}
```

##### Response Sample
I omit a part.
```json
{
    "errors": null,
    "rid": "11111111",
    "rval": {
        "totalNumEntries": 1,
        "values": [
            {
                "errors": null,
                "operationSucceeded": true,
                "reportDefinition": {
                    "accountId": 11111111,
                    "completeTime": "2020/05/22 14:43:20",
                    "dateRange": {
                        "endDate": "20371231",
                        "startDate": "19700101"
                    },
                    "fields": [
                        "COST",
                        ...
                    ],
                    "filters": [
                        {
                            "field": "COST",
                            "reportOperator": "NOT_EQUALS",
                            "value": [
                                "100"
                            ]
                        }
                    ],
                    "reportCompressType": "ZIP",
                    "reportDateRangeType": "CUSTOM_DATE",
                    "reportDownloadEncode": "UTF-8",
                    "reportDownloadFormat": "CSV",
                    "reportIncludeDeleted": "TRUE",
                    "reportIncludeZeroImpressions": "TRUE",
                    "reportJobErrorDetail": null,
                    "reportJobId": 11111111,
                    "reportJobStatus": "COMPLETED",
                    ...
                }
            }
        ]
    }
}
```

#### 4.	Download Report
Use download of ReportDefinitionService.  
Download report from ReportList.  

##### Request Sample
```json
{
  "accountId": 11111111,
  "reportJobId": 11111111
}
```

##### Response Sample
If no date, it looks like this.
```.csv
Cost,Impressions,Clicks,CTR,Avg. CPC,Avg. Position,Tracking URL,Conversions,Conv. Rate,Conv. Value,Cost Per Conv.,Value Per Conv.,Network,ClickType,Device,Day,Day of week,Quarter,Year,Month,Month of Year,Week,Hour of day
0,0,0,0.0000,0.0000,--,--,0.0000,--,0.0000,--,0.0000,--,--,--,--,--,--,--,--,--,--,--
```
