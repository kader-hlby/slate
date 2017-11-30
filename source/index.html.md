---
title: API Reference

#language_tabs: # must be one of https://git.io/vQNgJ

search: true
---

# Introduction

Welcome to the Knolskape API! You can use our API to access simulations API endpoints.


# Services

## Get All Services names with Simulation names

> Example Response:

```json
[
  {
      "serviceName": "bybhtml",
      "simulationName": "BYB V2"
  },
  {
      "serviceName": "cq-v2",
      "simulationName": "ChangeQuest v2"
  },
  {
      "serviceName": "ileadhtml",
      "simulationName": "iLead V2"
  }
]
```

This endpoint retrieves all Services names with Simulation names.

### HTTP Request

`GET https://api-test.knolskape.com/ct/simulations`

### Query Parameters

Parameter  | Description
---------  | -----------
platformId | -----------


# Candidates

## Register User

> Example Request:

```json
{
  "projectId": 125,
  "users": [
    {
      "id":1,
      "email": "accendouser1@mailinator.com",
      "name":"accendouser name",
      "redirectUrl":"http://kaliber.com/redirect",
      "callbackUrl":"http://kaliber.com/callback?token=f8XvlPhHpBcYVg7Pv9jBXVDDejNLyO12EgqWTomwh3th4tpYFyiORforoeqz"
    }
  ],
  "services": [
    "ilead",
    "cq-v2"
  ]
}
```

> Example Response:

```json
[
  {
    "service": "ilead",
    "users": [
      {
        "email": "accendouser1@mailinator.com",
        "link": "https://accounts.knolskape.com/ct-simulation?custom_token={custom_token1}",
        "token": "{custom_token1}"
      }
    ]
  },
  {
    "service": "cq-v2",
    "users": [
      {
        "email": "accendouser1@mailinator.com",
        "link": "https://accounts.knolskape.com/ct-simulation?custom_token={custom_token2}",
        "token": "{custom_token2}"
      }
    ]
  }
]
```

This endpoint registers users to a list of simulations.

### HTTP Request

`POST https://api-test.knolskape.com/ct/simulations/register`

### Query Parameters

Parameter  | Description
---------  | -----------
platformId | -----------

### Response Parameters

Parameter   | Description
---------   | -----------
projectId   | -----------
users       | -----------
services    | -----------

## Get Simulation Status and Scores By User id

> Example Response:

```json
{
    "metrics": [
        {
            "key": "status",
            "name": "Status"
        },
        {
            "key": "rank",
            "name": "Rank"
        },
        {
            "key": "noOfConversion",
            "name": "No. of Conversions"
        },
        {
            "key": "aggregateScore",
            "name": "Weighted Average Adoption"
        },
        {
            "key": "percentile",
            "name": "Average Adoption (percentile)"
        },
        {
            "key": "avgAdoption",
            "name": "Average Adoption"
        },
        {
            "key": "progress",
            "name": "Progress (in days)"
        },
        {
            "key": "timeLeft",
            "name": "Time Remaining (90 mins)"
        }
    ],
    "metricsData": [
        {
            "tokenId": "BnUny897Ywna3ezJzef8RuhxaNbUboxD",
            "status": "COMPLETED",
            "timeLeft": "88:21",
            "avgAdoption": "24.33",
            "progress": "14",
            "noOfConversion": "1",
            "aggregateScore": "20.94",
            "percentile": "7.51",
            "competency": "7.51",
            "rank": 1,
            "startedAt": 1505128287,
            "completedAt": 1605128302
        }
    ]
}
```

### HTTP Request

`GET https://api-test.knolskape.com/ct/simulation/{{simulation}}/metrics/project/{{projectIid}}/user/{{userId}}?platformId=2`

This endpoint retrieves Simulation Status and Scores for a specific user.

### Query Parameters

Parameter  | Description
---------  | -----------
platformId | -----------

### Response Parameters

Parameter   | Description
---------   | -----------
simulation  | -----------
projectIid  | -----------
userId      | -----------
## Get Simulation Status and Scores By Project id

> Example Response:

```json
{
    "metrics": [
        {
            "key": "status",
            "name": "Status"
        },
        {
            "key": "rank",
            "name": "Rank"
        },
        {
            "key": "noOfConversion",
            "name": "No. of Conversions"
        },
        {
            "key": "aggregateScore",
            "name": "Weighted Average Adoption"
        },
        {
            "key": "percentile",
            "name": "Average Adoption (percentile)"
        },
        {
            "key": "avgAdoption",
            "name": "Average Adoption"
        },
        {
            "key": "progress",
            "name": "Progress (in days)"
        },
        {
            "key": "timeLeft",
            "name": "Time Remaining (90 mins)"
        }
    ],
    "metricsData": [
        {
            "tokenId": "oBk4PdXHcbGXWcKuNCMnFWCUTTpPnxoA",
            "status": "STARTED",
            "startedAt": null,
            "completedAt": null
        },
        {
            "tokenId": "ZywFBkgDmQtaS8uxB9KaWfUGZcodzCEq",
            "status": "NOT_STARTED",
            "startedAt": null,
            "completedAt": null
        },
        {
            "tokenId": "BnUny897Ywna3ezJzef8RuhxaNbUboxD",
            "status": "STARTED",
            "timeLeft": "88:21",
            "avgAdoption": "24.33",
            "progress": "14",
            "noOfConversion": "1",
            "aggregateScore": "20.94",
            "percentile": "7.51",
            "competency": "7.51",
            "rank": 1,
            "startedAt": 1505128287,
            "completedAt": null
        },
    ]
}
```

### HTTP Request

`GET https://api-test.knolskape.com/ct/simulation/{{simulation}}/metrics/project/{{projectIid}}?platformId=2`

This endpoint retrieves Simulation Status and Scores for all Users in a specific Project. 

### Query Parameters

Parameter  | Description
---------  | -----------
platformId | -----------

### Response Parameters

Parameter   | Description
---------   | -----------
simulation  | -----------
projectIid  | -----------

