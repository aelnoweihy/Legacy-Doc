## Endpoints
| Verb | Endpoint | Production | Dev |
|------|----------|------------|-----|
| GET | [api/distr-inactive-users/{distrId}](#apidistr-inactive-usersdistrid) | Y | Y |
| GET | [api/userpending-bulk-v2/{userID}](#apiuserpending-bulk-v2userid) | Y | Y |
| GET | [api/distr-active-users/{distrId}](#apidistr-inactive-users-distrid) | Y | Y |


### api/distr-inactive-users/{distrId}
**Purpose:** Gets all inactive users for the currently logged in user tree

**DB Mapping:** [Egy_ReportDb/MYPHONE_TEST].[dbo].[DISTR_INACTIVE_USERS]

**URI Parameter:** userId = distrId of the current logged in user

**Status Codes:** 

- 200 Ok
- 404 Not Found


**Sample Output** 
```
[
    {
        "distr_id": "10409502",
        "distr_name": "مجدى عباس حامد",
        "M_RATIO": 6.0000,
        "COUNT21": 0,
        "per_bp": 904.0000,
        "PGROUP_BP": 904.0000,
        "TOTAL_BP": 904.0000,
        "area_name": "الزيتون",
        "TELEPHONE": "01012100546"
    },
    {
        "distr_id": "73005720",
        "distr_name": "محمود مصطفي عبدالمنعم عبدلله",
        "M_RATIO": 12.0000,
        "COUNT21": 0,
        "per_bp": 2661.0000,
        "PGROUP_BP": 3962.0000,
        "TOTAL_BP": 3962.0000,
        "area_name": "أسيوط",
        "TELEPHONE": "01090310729"
    }
]

```


### api/userpending-bulk-v2/{userId}

**Purpose:** Gets all pending salesorders related to the currently logged in mobile user, including HC and BNS records

**DB Mapping:** [Egy_ReportDb/MYPHONE_TEST].[dbo].[USERPENDING_BULK_V2]

**URI Parameter:** userId = distrId of the current logged in user

**Status Codes:** 

- 200 Ok
- 404 Not Found

**Note:** 
- Displays HC and BNS records
- This is the fixed version

**Sample Output** 
```
[
    {
        "DOC_ID": "990003055504",
        "SO_INV_TYPE": "CR",
        "DISTR_ID": "99048038",
        "DISTRNAME": "حنان احمد الطيب محمد",
        "COUNTER": "0001",
        "ITEM_ID": "BNS",
        "ITEMNAME": "خصم مكافأه",
        "QTY_REQ": 1.000,
        "UNIT_PRICE": null,
        "TOT_PRICE": null,
        "ITEM_BP": 0.0,
        "TOTAL_BP": 0.0,
        "DOC_DATE": "2025-05-18",
        "ADD_TIME": "13:41:15",
        "AREMARKS": "طلبية علا زكى 99479700فون المستلم01282452499كوم امبو البلد، النجاجرة ،شا ع الكنيسة ، بجوار جامع التوبة ،تنزيل التنشيط وهدايا النقاط ال350 نقطةالنجاجرة ،شارع الكنيسة ، بجوار جامع التوبة",
        "STORE_ID": "37",
        "ADELIVERY": "1/1",
        "CUST_ID": "99479700"
    },
    {
        "DOC_ID": "990003055504",
        "SO_INV_TYPE": "HC",
        "DISTR_ID": "99479700",
        "DISTRNAME": "علا زكى صغير بغدادى",
        "COUNTER": "0001",
        "ITEM_ID": "3264",
        "ITEMNAME": "مزيل بقع الدهون من اواني الطهي باور 500 مل  شكل جديد",
        "QTY_REQ": 8.000,
        "UNIT_PRICE": 0.000,
        "TOT_PRICE": 0.000,
        "ITEM_BP": 0.0,
        "TOTAL_BP": 0.0,
        "DOC_DATE": "2025-05-18",
        "ADD_TIME": "13:41:15",
        "AREMARKS": "0",
        "STORE_ID": "37",
        "ADELIVERY": "1/1",
        "CUST_ID": "99479700"
    }
]
```
### api/distr-active-users/{distrId}
**Purpose:** Gets all active users for the currently logged in user tree

**DB Mapping:** [Egy_ReportDb/MYPHONE_TEST].[dbo].[DISTR_ACTIVE_USERS]

**URI Parameter:** userId = distrId of the current logged in user

**Status Codes:** 

- 200 Ok
- 404 Not Found


**Sample Output** 
```
[
    {
        "distr_id": "10409502",
        "distr_name": "مجدى عباس حامد",
        "M_RATIO": 0.0000,
        "COUNT21": 0,
        "per_bp": 10.0000,
        "PGROUP_BP": 10.0000,
        "TOTAL_BP": 10.0000,
        "area_name": "الزيتون",
        "TELEPHONE": "01012100546"
    },
    {
        "distr_id": "73005720",
        "distr_name": "محمود مصطفي عبدالمنعم عبدلله",
        "M_RATIO": 0.0000,
        "COUNT21": 0,
        "per_bp": 10.0000,
        "PGROUP_BP": 10.0000,
        "TOTAL_BP": 10.0000,
        "area_name": "أسيوط",
        "TELEPHONE": "01090310729"
    }
]

```
