# Bulk-Related Doc

**Prod URL:**  http://mywayegypt-api.azurewebsites.net/
**Dev URL:**  http://mywayegypt-api-devenv.azurewebsites.net/

## Endpoints
| Verb | Endpoint | Production | Dev |
|------|----------|------------|-----|
| GET  | [userinvoices](#apiuserinvoicesuseridapi/userinvoices/{userId}) | Y | N |
| GET  | api/userinvoices-v2/{userId} | Y | Y |
| GET  | api/userpending/{userId} | Y | Y |
| GET  | api/userpending-bulk/{userId} | Y | N |
| POST | api/editvou-bulk/{doc_id}/{distr_id}/{store_id}/{so_type} | Y | N |

## api/userinvoices/{userId}

**Purpose:** Gets all invoices related to this user

**DB Mapping:** [Egy_ReportDb].[dbo].[USERINVOICES] & [Egy_ReportDb].[dbo].[USERINVOICES_LASTDAY]

**URI Parameter:** userId = distrId of the current logged in user

**Status Codes:** 

- 200 Ok
- 404 Not Found

**Note:** 
- This API does not display HC items or BNS items
- Distr used: 99471434

**Sample Output** 
```
[
    {
        "DOC_ID": "390880039178",
        "FLAG_TYPE": "CR",
        "DISTR": "99471434",
        "DISTR_NAME": "عبير أحمد عبدالعال أحمد",
        "COUNTER": "0001",
        "ITEM_ID": "1523",
        "ITEM_NAME": "كريم تصفيف كيراكيور بالكيراتين 150 جم / حجم وشكل جديد",
        "PRICE": 51.25,
        "QTY": 1.0,
        "NET_TOTAL": 51.25,
        "ITEM_BP": 13.0,
        "TOTAL_BP": 13.0,
        "DOC_DATE": "2025-05-17",
        "DS_SHIPMENT": "390880024696",
        "SHIPMENT_STATUS": "2",
        "DLV_DATE": "0000-00-00",
        "COMP_NAME": "ماى واى",
        "REF_NO": "",
        "STORE_ID": "39",
        "ADELIVERY": "1/1",
        "REF_NO_87": "0",
        "CUST_ID": "99471434"
    },
    {
        "DOC_ID": "390880039178",
        "FLAG_TYPE": "CR",
        "DISTR": "99471434",
        "DISTR_NAME": "عبير أحمد عبدالعال أحمد",
        "COUNTER": "0002",
        "ITEM_ID": "1572",
        "ITEM_NAME": "مخمرية العروسة لتنعيم و تعطير الشعر",
        "PRICE": 31.5,
        "QTY": 1.0,
        "NET_TOTAL": 31.5,
        "ITEM_BP": 8.0,
        "TOTAL_BP": 8.0,
        "DOC_DATE": "2025-05-17",
        "DS_SHIPMENT": "390880024696",
        "SHIPMENT_STATUS": "2",
        "DLV_DATE": "0000-00-00",
        "COMP_NAME": "ماى واى",
        "REF_NO": "",
        "STORE_ID": "39",
        "ADELIVERY": "1/1",
        "REF_NO_87": "0",
        "CUST_ID": "99471434"
    }
]   
```
## api/userinvoices-v2/{userId}

**Purpose:**  Gets all invoices made by the currently logged in user, including BNS, and HC items

**DB Mapping:** [Egy_ReportDb].[dbo].[USERINVOICES_BULK] & [Egy_ReportDb].[dbo].[USERINVOICES_LASTDAY_BULK]

**URI Parameter:** userId = distrId of the current logged in user

**Status Codes:** 

- 200 Ok
- 404 Not Found

**Note:** 
- This Api displays BNS and HC items
- Test distr BNS 99471434, HC 99256576

**Sample Output** 
```
[
    {
        "DOC_ID": "390880039178",
        "FLAG_TYPE": "CR",
        "DISTR": "99471434",
        "DISTR_NAME": "عبير أحمد عبدالعال أحمد",
        "COUNTER": "0001",
        "ITEM_ID": "BNS",
        "ITEM_NAME": "خصم مكافأه",
        "PRICE": 33.0,
        "QTY": 1.0,
        "NET_TOTAL": 33.0,
        "ITEM_BP": 0.0,
        "TOTAL_BP": 0.0,
        "DOC_DATE": "2025-05-17",
        "DS_SHIPMENT": "390880024696",
        "SHIPMENT_STATUS": "2",
        "DLV_DATE": "0000-00-00",
        "COMP_NAME": "ماى واى",
        "STORE_ID": "39",
        "ADELIVERY": "1/1",
        "REF_NO": "0",
        "CUST_ID": "99471434"
    },
    {
        "DOC_ID": "101628013700",
        "FLAG_TYPE": "HC",
        "DISTR": "99256576",
        "DISTR_NAME": "ياسمين فرحات عبدالجواد",
        "COUNTER": "0001",
        "ITEM_ID": "3342",
        "ITEM_NAME": "كلين منظف المفروشات بدون رغوة 660 مل",
        "PRICE": 0.0,
        "QTY": 5.0,
        "NET_TOTAL": 0.0,
        "ITEM_BP": 0.0,
        "TOTAL_BP": 0.0,
        "DOC_DATE": "2025-05-11",
        "DS_SHIPMENT": "101628011671",
        "SHIPMENT_STATUS": "703",
        "DLV_DATE": "2025-05-11",
        "COMP_NAME": "ماى  واى",
        "STORE_ID": "01",
        "ADELIVERY": "1/1",
        "REF_NO": "0",
        "CUST_ID": "0"
    }
]
```

## api/userpending/{userId}

**Purpose:** Gets all pending salesorders by the currently logged in user

**DB Mapping:** [Egy_ReportDb].[dbo].[USERPENDING]

**URI Parameter:** userId = distrId of the current logged in user

**Status Codes:** 

- 200 Ok
- 404 Not Found

**Note:** 
- Does not display BNS or HC items

**Sample Output** 
```
[
    {
        "DOC_ID": "990003055504",
        "SO_INV_TYPE": "CR",
        "DISTR_ID": "99479700",
        "DISTRNAME": "علا زكى صغير بغدادى",
        "COUNTER": "0001",
        "ITEM_ID": "5866",
        "ITEMNAME": "Perfume Don't Stop 55 ML",
        "QTY_REQ": 2.000,
        "UNIT_PRICE": 119.250,
        "TOT_PRICE": 238.500,
        "ITEM_BP": 30.0,
        "TOTAL_BP": 60.0,
        "DOC_DATE": "2025-05-18",
        "ADD_TIME": "13:41:15",
        "AREMARKS": "طلبية علا زكى 99479700فون المستلم01282452499كوم امبو البلد، النجاجرة ،شا ع الكنيسة ، بجوار جامع التوبة ،تنزيل التنشيط وهدايا النقاط ال350 نقطةالنجاجرة ،شارع الكنيسة ، بجوار جامع التوبة",
        "STORE_ID": "37",
        "ADELIVERY": "1/1",
        "CUST_ID": "99479700"
    },
    {
        "DOC_ID": "990003055504",
        "SO_INV_TYPE": "CR",
        "DISTR_ID": "99479700",
        "DISTRNAME": "علا زكى صغير بغدادى",
        "COUNTER": "0002",
        "ITEM_ID": "5922",
        "ITEMNAME": "كولونيا اسنشيال 115 مل",
        "QTY_REQ": 3.000,
        "UNIT_PRICE": 47.000,
        "TOT_PRICE": 141.000,
        "ITEM_BP": 12.0,
        "TOTAL_BP": 36.0,
        "DOC_DATE": "2025-05-18",
        "ADD_TIME": "13:41:15",
        "AREMARKS": "طلبية علا زكى 99479700فون المستلم01282452499كوم امبو البلد، النجاجرة ،شا ع الكنيسة ، بجوار جامع التوبة ،تنزيل التنشيط وهدايا النقاط ال350 نقطةالنجاجرة ،شارع الكنيسة ، بجوار جامع التوبة",
        "STORE_ID": "37",
        "ADELIVERY": "1/1",
        "CUST_ID": "99479700"
    }
]
```

## api/userpending-bulk/{userId}

**Purpose:** Gets all pending salesorders related to the currently logged in mobile user, including HC and BNS records

**DB Mapping:** [Egy_ReportDb].[dbo].[USERPENDING_BULK]

**URI Parameter:** userId = distrId of the current logged in user

**Status Codes:** 

- 200 Ok
- 404 Not Found

**Note:** 
- Displays HC and BNS records

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
## api/editvou-bulk/{doc_id}/{distr_id}/{store_id}/{so_type}

**Purpose:** Deletes normal salesorders and deletes from bulk salesorders with reconfiguring ADELIVERY sequence

**DB Mapping:** [Egy_Coordinator].[dbo].[X], where X refers to a specific sproc based on store_id
| StoreId | Sproc |
|---------|-------|
|01|EditVou_MYPHONE_BULK|
|68|EditVou_MANSORA_CREDIT_BULK|
|71|EditVou_BEN_CREDIT_BULK|
|72|EditVou_DELTA_CREDIT_BULK|
|69|EditVou_ALEX_CREDIT_BULK|
|73|EditVou_ASSIUT_BULK|
|70|EditVou_LUXOR_BULK|
|59|EditVou_SOHAG_BULK|
|05|EditVou_DOMYAT_BULK|
|33|EditVou_SUEZ_BULK|
|06|EditVou_MENYA_BULK|
|14|EditVou_ISM_BULK|
|64|EditVou_QENA_BULK|
|37|EditVou_ASWAN_BULK|
|67|EditVou_HURGHADA_BULK|
|39|EditVou_MATROH_BULK|
|66|EditVou_FAYOUM_BULK|
|03|EditVou_PSAID_BULK|

**URI Parameter:** 
- doc_id for the desired document
- distr_id distr whom the salesorder is made for (AP.DISTR_ID)
- store_id store on which the document is made at
- so_type CA or CR -- only CR for now

**Status Codes:** 

- 200 Ok
- 404 Not Found

**Note:** 

**Sample Output** 
"DELETED"
