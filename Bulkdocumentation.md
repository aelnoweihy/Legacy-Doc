# Bulk-Related Doc

**Prod URL:**  http://mywayegypt-api.azurewebsites.net/

**Dev URL:**  http://mywayegypt-api-devenv.azurewebsites.net/

## Endpoints
| Verb | Endpoint | Production | Dev |
|------|----------|------------|-----|
| GET  | [api/userinvoices/{userId}](#apiuserinvoicesuserid) | Y | N |
| GET  | [api/userinvoices-v2/{userId}](#apiuserinvoices-v2userid) | Y | Y |
| GET  | [api/userpending/{userId}](#apiuserpendinguserid) | Y | Y |
| GET  | [api/userpending-bulk/{userId}](#apiuserpending-bulkuserid) | Y | Y |
| POST | [api/editvou-bulk/{doc_id}/{distr_id}/{store_id}/{so_type}](#apieditvou-bulkdoc_iddistr_idstore_idso_type) | Y | N |
| PUT  | [api/soBulk](#apisobulk) | Y | Y |
| PUT  | [api/memregister_no_so/{leaderId}/{ds_shipment_place}/{areaId_8k}/{spname}/{inv_type}/{store_id}](#apimemregister_no_soleaderidds_shipment_placeareaid_8kspnameinv_typestore_id) | Y | Y |

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
- Still needs replication work. Ednpoint specs will be kept

**Sample Output** 
"DELETED"


## api/soBulk

**Verb:** PUT

**Purpose:** Creates a bulk salesorder

**DB Mapping:** AP, AQ, DSAP3, A9, AA

**URI Parameter:** N/A

**NOTES:**
- a9master.USER_ID: it's always the currently logged in user.
- a9master.CUS_VEN_ID: it's always the distr who the user makes the salesorder for
- apmaster.CUST_ID: it's the user who's gonna receive the shipment
- While populating the API, here's the mapping of values:
	- apmaster.DISTR_ID = a9master.CUS_VEN_ID
 	- apmaster.USER_ID = a9master.USER_ID
- If we want to add a new membership during a bulk operation, here's the API flow:
	- Use 


**Request Body:** 
```
{
    "batch": [
        {
            "a9master": {
                "STORE_ID": "01",
                "BRANCH_ID": "10",
                "CUS_VEN_ID": "00000001",
                "USER_ID": "003"
            },
            "apmaster": {
                "STORE_ID": "01",
                "SO_INV_TYPE": "CR",
                "GROSS_TOTAL": 23100,
                "NET_TOTAL": 23100,
                "PRJ_ID": "AAAA",
                "DS_SHIPMENT_COMP": "00000001",
                "DS_SHIPMENT_PLACE": "01",
                "AREMARKS": "Test salesorder",
                "SHIPMTHD_A": "{for bonus}",
                "SHIPMTHD_L": "{for backorder}",
		"CUST_ID" : "00000001"
            },
            "aadetail": [
                {
                    "ITEM_ID": "4227",
                    "QTY": 1,
                    "DS_SHIPMENT_COMP": "00000001",
                    "DS_SHIPMENT_PLACE": "01"
                }
            ],
            "aqdetail": [
                {
                    "ITEM_ID": "4227",
                    "QTY_REQ": 1,
                    "UNIT_PRICE": 23100,
                    "NET_PRICE": 23100,
                    "TOT_PRICE": 23100,
                    "ITEM_BP": 8,
                    "ITEM_BV": 19200
                },
                {
                    "ITEM_ID": "90",
                    "QTY_REQ": 1,
                    "UNIT_PRICE": 23100,
                    "NET_PRICE": 23100,
                    "TOT_PRICE": 23100,
                    "ITEM_BP": 8,
                    "ITEM_BV": 19200
                }
            ],
            "backorder": [
                {
                    "DOC_ID": "100011005285",
                    "ITEM_ID": "9186",
                    "FINALQTY": 1,
                    "GIFT_TYPE": "0"
                }
            ],
            "ap3": [
	        {
	            "DISTR_ID": "10191974",
	
	            "S_SERIAL" : "BONUS VALUE IN STRING"
	        },
	        {
	            "DISTR_ID": "10000124",
	
	            "S_SERIAL" : "BONUS VALUE IN STRING"
	
	        }
	    ]
        }
    ],
    "storeId":"01"
}
```
**Output:**

| Code | Message                                                                   |
| ---- | ------------------------------------------------------------------------- |
| 201  | Returns a list of sales order DOC_ID<br>[<br>    "9900031039365"<br>]<br> |
| 500  | An error occured while processing the transaction.                        |

## api/memregister_no_so/{leaderId}/{ds_shipment_place}/{areaId_8k}/{spname}/{inv_type}/{store_id}

**Verb:** PUT

**Purpose:** Creates a new membership without sales order

**DB Mapping:** AZ1, DISTR_SHIPPL

**URI Parameter:** same parameters as the normal memregister-v2 API.

**Sample Call:**
- **URI**: api/memregister_no_so/00000001/100052/36/الخانكه/CR/01
- **Request Body:**
```
{
	"SERVICE_CENTER":"11",
	"SPONSOR_ID" : "00000001",
	"FAMILY_ANAME":"النويهى",
	"ANAME":"02عبدالرحمن أيمن",
	"DISTR_IDENT":"123qwe102",
	"BIRTH_DATE": "1994-07-18",
	"E_MAIL":"abdelrahmanayman48@gmail.com",
	"TELEPHONE":"01141120200",
	"ADDRESS":"123 test",
    "AREA_ID": "01"
}
```

**Output:** 
```
{
    "id": "99479139"
}
```

# Flow of members within bulk:
- First we call [api/memregister_no_no](#apimemregister_no_soleaderidds_shipment_placeareaid_8kspnameinv_typestore_id).
- We store the return as an array to be fed into [api/soBulk](#apisobulk) as the following sample
```
{
    "batch": [
        {
            "a9master": {
                "STORE_ID": "01",
                "BRANCH_ID": "10",
                "CUS_VEN_ID": "distrId output from memregister_no_so",
                "USER_ID": "current logged in user"
            },
            "apmaster": {
                "STORE_ID": "01",
                "SO_INV_TYPE": "CR",
                "GROSS_TOTAL": 20,
                "NET_TOTAL": 20,
                "PRJ_ID": "AAAA",
                "DS_SHIPMENT_COMP": "100001",
                "DS_SHIPMENT_PLACE": "100052",
                "AREMARKS": "New Membership",
                "SHIPMTHD_A": "",
                "SHIPMTHD_L": "",
		        "CUST_ID" : "proper cust_id"
            },
            "aadetail": [
                {
                    "ITEM_ID": "99m",
                    "QTY": 1,
                    "DS_SHIPMENT_COMP": "00000001",
                    "DS_SHIPMENT_PLACE": "01"
                }
            ],
            "aqdetail": [
                {
                    "ITEM_ID": "99m",
                    "QTY_REQ": 1,
                    "UNIT_PRICE": 20,
                    "NET_PRICE": 20,
                    "TOT_PRICE": 20,
                    "ITEM_BP": 0,
                    "ITEM_BV": 0
                }
            ],
            "backorder": [],
            "ap3": []
        },
--next sales order in bulk 
    ],
    "storeId":"01"
}
```
- To get the proper value of the 99m, call API: https://mmaas.codev.solutions/api/items/99 or http://159.65.87.196:5000/api/items/99  
