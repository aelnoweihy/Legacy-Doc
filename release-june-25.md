## Endpoints
| Verb | Endpoint | Production | Dev |
|------|----------|------------|-----|
| GET | [api/distr-inactive-users/{distrId}](#apidistr-inactive-usersdistrid) | Y | Y |
| GET | [api/userpending-bulk-v2/{userID}](#apiuserpending-bulk-v2userid) | Y | Y |
| GET | [api/distr-active-users/{distrId}](#apidistr-active-usersdistrid) | Y | Y |


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
        "distr_id": "52063675",
        "distr_name": "افراج حموده حموده يوسف السمار",
        "M_RATIO": 12.0000,
        "area_name": "الاسكندرية",
        "TELEPHONE": "01210449721",
        "LAST_INV_DATE": "2025-05-31"
    },
    {
        "distr_id": "05067970",
        "distr_name": "ايمان محمد أحمد منصور",
        "M_RATIO": 3.0000,
        "area_name": "دمياط",
        "TELEPHONE": "01067862757",
        "LAST_INV_DATE": "2025-05-26"
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
        "distr_id": "03070536",
        "distr_name": "توفيق عبدالحميد سعد القلينى",
        "TOTAL_BP": 30.0000,
        "area_name": "بورسعيد",
        "TELEPHONE": "01223881399"
    },
    {
        "distr_id": "05073821",
        "distr_name": "محمد عبداللطيف محمد عبداللطيف الشربينى",
        "TOTAL_BP": 27.0000,
        "area_name": "دمياط",
        "TELEPHONE": "01012212284"
    }
]

```
