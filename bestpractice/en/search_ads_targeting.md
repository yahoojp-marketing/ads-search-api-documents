# Targeting [Search Ads]
## What is targeting ?
<a href="https://ads-help.yahoo-net.jp/s/article/H000045040?language=en_US">Targeting</a> is a feature that enables displaying advertisements to the right users at the right time.<br>
In search ads, the following targeting options are available:<br>
* “LOCATION” （Geo targeting）
* “SCHEDULE”（Day of week/Hours targeting）
* “PLATFORM” (Device targeting)

## How to operate from Search Ads API
To utilize targeting in the Search Ads API, the following three services are used:

##### 1. CampaignService
You can get/add/set/remove information related to campaigns.

##### 2. DictionaryService（only if you want to specify location targeting）
You can get a list of location information.

##### 3. CampaignTargetService
You can get/add/set/remove information related to the targeting settings of a campaign.

These services provide the necessary functionalities for managing targeting in the Search Ads API.

## Scenerio Sample
Company A will utilize the Search Ads API to perform campaign creation and targeting setup.<br>
The targeting settings in this scenario are as follows:<br>
Note: Bid adjustment values are represented as decimal numbers ranging from 0.10 to 10.00. (100% is represented as 1).<br>
　　　For example, a +30% adjustment would be 1.3, and a -90% adjustment would be 0.1.

<table class="standard">
  <tr>
　　<th>Target Type</th>
　　<th>Targeting</th>
　　<th>Bid adjustment rate</th>
　</tr>
　<tr>
　　<td>Day of week/Hours targeting</td>
　　<td>From 7 PM to 12 AM on Saturdays</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>Day of week/Hours targeting</td>
　　<td>From 7 PM to 12 AM on Sundays</td>
　　<td>1.3</td>
　</tr>
　<tr>
　　<td>Geo targeting</td>
　　<td>Tokyo, delivery</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>Geo targeting</td>
　　<td>Kanagawa Prefecture, Yokohama City, delivery</td>
　　<td>0.9</td>
　</tr>
　<tr>
　　<td>Geo targeting</td>
　　<td>Tokyo, Chiyoda Ward, delivery exclusion</td>
　　<td></td>
　</tr>
　<tr>
　　<td>Device targeting</td>
　　<td>Smartphone</td>
　　<td>1</td>
　</tr>
　<tr>
　　<td>Device targeting</td>
　　<td>Tablet</td>
　　<td>0.8</td>
　</tr>
</table>
<br>

#### 1.      Create Campaign
The CampaignService:add method is used to create a campaign.

##### Request Sample
```json
{
  "accountId": 11111111,
  "operand":[{
    "campaignName": "TargetTestCampaign",
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

##### Response Sample
Note: Due to length constraints, some parts have been omitted.
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
          "campaignName": "TargetTestCampaign",
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

#### 2.	Get a List of Geographic Locations
The DictionaryService:getGeographicLocation method is used to retrieve a list of geographic locations.<br>
The codes obtained from this list will be used to specify geographic targeting in the subsequent steps.


##### Request Sample
```json
{
  "lang": "EN"
}
```

##### Response Sample
Note: Due to length constraints, some parts have been omitted.
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
              "fullName": "Asahikawa,Hokkaido",
              "geographicLocationStatus": "ACTIVE",
              "name": "Asahikawa",
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
                  "fullName": "Akishima,Tokyo",
                  "geographicLocationStatus": "ACTIVE",
                  "name": "Akishima",
                  "order": "1200000100",
                  "parent": "JP-13"
              },
              ...
              {
                  "child": null,
                  "code": "JP-13-0005",
                  "fullName": "Chiyoda,Tokyo",
                  "geographicLocationStatus": "ACTIVE",
                  "name": "Chiyoda",
                  "order": "1200003300",
                  "parent": "JP-13"
              },
              ...
              {
                  "child": null,
                  "code": "JP-13-0025",
                  "fullName": "Meguro,Tokyo",
                  "geographicLocationStatus": "ACTIVE",
                  "name": "Meguro",
                  "order": "1200005300",
                  "parent": "JP-13"
              }
            ],
            "code": "JP-13",
            "fullName": "Tokyo",
            "geographicLocationStatus": "ACTIVE",
            "name": "Tokyo",
            "order": "1200000000",
            "parent": null
          },
          "operationSucceeded": true
        },
        ...
            {
                "child": null,
                "code": "JP-14-0025",
                "fullName": "Yokohama,Kanagawa",
                "geographicLocationStatus": "ACTIVE",
                "name": "Yokohama",
                "order": "1300002900",
                "parent": "JP-14"
            }
          ...
          ],
          "code": "JP-47",
          "fullName": "Okinawa",
          "geographicLocationStatus": "ACTIVE",
          "name": "Okinawa",
          "order": "4600000000",
          "parent": null
        },
        "operationSucceeded": true
      }
    ]
  }
}
```

#### 3.	Confirm Targeting Settings
Use the CampaignTargetService:get method to confirm the current targeting settings.<br>
By executing step 1, it can be confirmed that all devices are being targeted.

##### Request Sample
```json
{
  "accountId": 11111111,
  "campaignIds": [2222222]
}
```

##### Response Sample

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
          "campaignName": "TargetTestCampaign",
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
          "campaignName": "TargetTestCampaign",
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
          "campaignName": "TargetTestCampaign",
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

#### 4.	Update Targeting Settings
Use the CampaignTargetService:set method to update the targeting settings.<br>
In this case, we will update the device targeting. As confirmed in step 3, adjustments are necessary since device targeting is initially set during campaign creation.<br>
Adjust the bid adjustment for PC and tablets according to the scenario. (Note: Setting the bid adjustment to 0 will prevent the ads from being delivered).

##### Request Sample
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

##### Response Sample

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
          "campaignName": "TargetTestCampaign",
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
          "campaignName": "TargetTestCampaign",
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

#### 5.	Targeting Settings
Use the CampaignTargetService:add method to set the necessary day of the week and time zone targeting, as well as geographic targeting, for this scenario.

##### Request Sample
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

##### Response Sample

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
          "campaignName": "TargetTestCampaign",
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
          "campaignName": "TargetTestCampaign",
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
          "campaignName": "TargetTestCampaign",
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
          "campaignName": "TargetTestCampaign",
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
          "campaignName": "TargetTestCampaign",
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
