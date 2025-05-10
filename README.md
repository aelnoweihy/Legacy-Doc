# Preface
This document serves to document all APIs running for the production environment and dev environment.
# Domains
- **Production URL:** http://mywayegypt-api.azurewebsites.net/api/{endpoint}
- **Dev URL:** http://mywayegypt-api-devenv.azurewebsites.net/api/{endpoint}
# Databases Used
- **Production:**
	- Egy_Azure
	- Egy_ReportDb
- **Dev**:
	- Test_Db
# Tech Used
- ASP.NET 4.7
- Microsoft SQL Server
# Endpoint Table

| Method Verb | Endpoint                                                                                          | Dev | Prod | MobApp                                                                                                        |
| ----------- | ------------------------------------------------------------------------------------------------- | --- | ---- | ------------------------------------------------------------------------------------------------------------- |
| GET         | [[#areas]]                                                                                        | Y   | Y    | Y                                                                                                             |
| GET         | [[#areaid/{id}]]                                                                                  | Y   | Y    | Y                                                                                                             |
| GET         | [[#distrsummary/{id}]]                                                                            | Y   | Y    | Y                                                                                                             |
| POST        | [[#editvou/{doc_id}/{distr_id}/{store_id}/{so_type}]]                                             | Y   | Y    |                                                                                                               |
| GET         | [[#datetimenow]]                                                                                  | Y   | Y    | Y                                                                                                             |
| PUT         | [[#invoice]]                                                                                      | Y   | Y    |                                                                                                               |
| PUT         | [[#soBulk]]                                                                                       | Y   | Y    |                                                                                                               |
| POST        | [[#updatedelap/{doc_id}/{distr_id}/{store_id}/{so_type}]]                                         | Y   | Y    |                                                                                                               |
| GET         | [[#admin-fee-status/{distr_id}]]                                                                  | Y   | Y    |                                                                                                               |
| POST        | [[#updatedoneinv/{doc_id}/{distr_id}/{store_id}/{doc_type}]]                                      | Y   | Y    |                                                                                                               |
| GET         | [[#getBackOrderItemsNew/{distr_id}/{store_id}]]                                                   | Y   | Y    |                                                                                                               |
| GET         | [[#leaderverification/{leaderID}/{distrID}]]                                                      | Y   | Y    | Y                                                                                                             |
| GET         | [[#memberid/{id}]]                                                                                | Y   | Y    | Y                                                                                                             |
| GET         | [[#member_fees_verification/{distr_id}/{service_center}]]                                         | Y   | Y    | Y                                                                                                             |
| GET         | [[#deserve_bonus/{distr_id}]]                                                                     | Y   | Y    | Y                                                                                                             |
| PUT         | [[#memregister-v2/{leaderId}/{ds_shipment_place}/{areaId_8k}/{spname}/{inv_type}/{store_id}]]     | Y   | Y    |                                                                                                               |
| GET         | [[#heldItemReport/{distrID}]]                                                                     | Y   | Y    |                                                                                                               |
| GET         | [[#newmembers/{distrID}]]                                                                         | Y   | Y    | Y                                                                                                             |
| GET         | [[#distrratio/{distrID}]]                                                                         | Y   | Y    | Y                                                                                                             |
| GET         | [[#shipmentcompanies]]                                                                            | Y   | Y    | Not sure if used                                                                                              |
| GET         | [[#get_all_shipment_places]]                                                                      | Y   | Y    | Y                                                                                                             |
| GET         | [[#get_shipment_places_by_area_id/{areaID}]]                                                      | Y   | Y    | Y                                                                                                             |
| GET         | [[#get_shipment_places_by_distr_id/{distrID}]]                                                    | Y   | Y    | Y                                                                                                             |
| PUT         | [[#add_new_distr_shipment_place/{store_id}]]                                                      | Y   | Y    | Y                                                                                                             |
| DELETE      | [[#delete_distr_shipment_place_record/{id}]]                                                      | Y   | Y    | Unused                                                                                                        |
| GET         | [[#stock/{item_id}/{store_id}]]                                                                   | Y   | Y    | Y                                                                                                             |
| GET         | [[#getinvoicedetails/{doc_id}]]                                                                   | Y   | Y    | Y                                                                                                             |
| GET         | [[#getlateinvoices/{distr_id}]]                                                                   | Y   | Y    | Y                                                                                                             |
| GET         | [[#missingordamageditems/{distr_id}]]                                                             | Y   | Y    | Y                                                                                                             |
| GET         | [[#userpending/{userID}]]                                                                         | Y   | Y    | Y                                                                                                             |
| GET         | [[#userinvoices/{userID}]]                                                                        | Y   | Y    | Y                                                                                                             |
| GET         | [[#getPendingPoints/{distr_id}]]                                                                  | Y   | Y    |                                                                                                               |
| GET         | [[#getPersonalPoints/{distr_id}]]                                                                 | Y   | Y    |                                                                                                               |
| GET         | [[#api/invoices/{id}]]                                                                            | Y   | Y    |                                                                                                               |
| GET         | itemdetails                                                                                       | N   | N    | Removed                                                                                                       |
| GET         | allitemdetails                                                                                    | N   | N    | Removed                                                                                                       |
| GET         | newproducts                                                                                       | N   | N    | Removed                                                                                                       |
| GET         | getBackOrderItems                                                                                 | Y   | Y    | Depricated, use [[#getBackOrderItemsNew/{distr_id}/{store_id}]]                                               |
| GET         | [[#distrrepsummary/{distrID}]]                                                                    | Y   | Y    |                                                                                                               |
| GET         | [[#allmembers]]                                                                                   | Y   | Y    | Unused (takes ages)                                                                                           |
| GET         | [[#pending/{id}]]                                                                                 | Y   | Y    | Y                                                                                                             |
| GET         | [[#getshipment]]                                                                                  | Y   | Y    | not sure if used                                                                                              |
| GET         | [[#getshipmentbyplaceid/{dsShipment}]]                                                            | Y   | Y    | not sure if used                                                                                              |
| GET         | [[#getshipmentbyaname/{aname}]]                                                                   | Y   | Y    | not sure if used                                                                                              |
| GET         | [[#get_shiplent_places_by_record_id/{id}]]                                                        | Y   | Y    | not sure if used                                                                                              |
| GET         | [[#report_details/{id}]]                                                                          | Y   | Y    | not sure if used                                                                                              |
| GET         | [[#pendingmember/{userID}]]                                                                       | Y   | Y    | not sure if used                                                                                              |
| GET         | [[#memberpromo/{distr_id}]]                                                                       | Y   | Y    | not sure if used                                                                                              |
| GET         | cashBackOrder                                                                                     | N   | N    | doesn't exist                                                                                                 |
| GET         | [[#get-cash-backorder/{distr_id}/{store_id}]]                                                     | Y   | Y    | not sure if used                                                                                              |
| PUT         | insert_batch_sales_orders                                                                         | Y   | Y    | Depricated, use [[#soBulk]]                                                                                   |
| PUT         | memregister_no_so                                                                                 | Y   | Y    | Depricated, use [[#memregister-v2/{leaderId}/{ds_shipment_place}/{areaId_8k}/{spname}/{inv_type}/{store_id}]] |
| PUT         | memregister_ds                                                                                    | Y   | Y    | Depricated, use [[#memregister-v2/{leaderId}/{ds_shipment_place}/{areaId_8k}/{spname}/{inv_type}/{store_id}]] |
| PUT         | memregister_ds_8k                                                                                 | Y   | Y    | Depricated, use [[#memregister-v2/{leaderId}/{ds_shipment_place}/{areaId_8k}/{spname}/{inv_type}/{store_id}]] |
| PUT         | memregister                                                                                       | Y   | Y    | Depricated, use [[#memregister-v2/{leaderId}/{ds_shipment_place}/{areaId_8k}/{spname}/{inv_type}/{store_id}]] |
| Mix         | SPOT & GUEST METHODS                                                                              | Y   | Y    | Pending review                                                                                                |
| PUT         | [[#api/memregister-v3/{leaderId}/{ds_shipment_place}/{areaId_8k}/{spname}/{inv_type}/{store_id}]] | Y   | Y    | Same params as [[#memregister-v2/{leaderId}/{ds_shipment_place}/{areaId_8k}/{spname}/{inv_type}/{store_id}]]  |
|             |                                                                                                   |     |      |                                                                                                               |
# Endpoints
## areas
**Verb:** GET
**Purpose:** Queries db and returns a list of all areas
**DB Mapping:** ACC0118k
**URI Parameter:** N/A
**Output:**

| Status Code | Message/Body                                                                                                       |
| ----------- | ------------------------------------------------------------------------------------------------------------------ |
| 200         | Ok<br>returns a list of the following object<br>[ <br>   { <br>      aname : ### , <br>	  AREA_ID : ## <br>	}<br>] |
| 404         | Not found - no special message                                                                                     |

## areaid/{id}
**Verb:** GET
**Purpose:** Queries DB and returns a list of all areas
**DB Mapping:** ACC0118K
**URI Parameter:** id is a string corresponding to AREA_ID
**Output:**

| Status Code | Message/Body                                                                                                        |
| ----------- | ------------------------------------------------------------------------------------------------------------------- |
| 200         | Ok<br>A list of the following object:<br>[<br>   {<br>      aname:  {string}, <br>	  area_id: {string}<br>   }<br>] |
| 404         | Not found - no special message                                                                                      |

## distrsummary/{id}
**Verb:** GET
**Purpose:** Returns a summary of the points and reports for the distr
**DB Mapping:** distr_summary sproc
**URI Parameter:** id for distr_id
**Output:**

| Status Code | Message/Body                                                                                                                                                                                               |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 200         | Ok<br>A list of the following object:<br>{<br>  {<br>     distr_id: ,<br>	 name: ,<br>	 sponsor_id: ,<br>	 sponsor_name: ,<br>	 area: ,<br>	 count: ,<br>	 per_bp: ,<br>	 ratio: ,<br>	 sum: ,<br>  }<br>} |
| 404         | not found - no special message                                                                                                                                                                             |

## editvou/{doc_id}/{distr_id}/{store_id}/{so_type}
**Verb:** POST
**Purpose:** deletes a salesorder
**DB Mapping:** on cloud coordinator editvou per store available
**URI Parameter:** doc_id, distr_id, store_id, so_type
**Output:**

| Status Code | Message/Body                  |
| ----------- | ----------------------------- |
| 200         | Ok<br>"DELETED"               |
| 404         | not found, no special message |

## datetimenow
**Verb:** GET
**Purpose:** Gets the current UTC date and time +2 
**DB Mapping:** n/a
**URI Parameter:** n / a
**Output:** 200 - ok with datetime format
## invoice
**Verb:** PUT
**Purpose:** Creates a salesorder
**DB Mapping:** ACC011AP, AQ, AA, A9, DSAP3
**URI Parameter:** N/a
**Sample Request Body:** 
```
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
        "PRJ_ID": "9999",
        "DS_SHIPMENT_COMP": "00000001",
        "DS_SHIPMENT_PLACE": "01",
        "AREMARKS": "9",
        "RSRV_ID":"{TELEPHONE}"
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
        }
    ],
    "backorder": [
        {
            "DOC_ID": "100011005285",
            "ITEM_ID": "9186",
            "FINALQTY": 1.0,
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
```
**Output:**
Status Code: 201 - Created
```
{
    "id":"990003000001",
    "amt":60.75,
    "docDate":"2020-01-01",
    "addTime":"HH:mm:ss"
}
```
**Note:** AP table ADELIVERY will contain the string "1/1" to denote a single salesorder
## soBulk
**Verb:** PUT
**Purpose:** Creates a bulk salesorder
**DB Mapping:** AP, AQ, DSAP3, A9, AA
**URI Parameter:** N/A
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

**Note:** AP table ADELIVERY will contain the string a string to mark the bulk sales order as a fraction of total sales orders within the single call IE (6/1, 6/2..6/6)
## updatedelap/{doc_id}/{distr_id}/{store_id}/{so_type}
**Verb:** POST
**Purpose:** updates deleted columns
**DB Mapping:** UPDATE_DEL_AP sproc
**URI Parameter:** doc_id, distr_id, store_id, so_type
**Output:** 200-Ok
## admin-fee-status/{distr_id}
**Verb:** GET
**Purpose:** Checks if administration fees are applicable 
**DB Mapping:** ADMIN_EXPENSES sproc
**URI Parameter:** distr_id
**Output:**

| Status Code | Message/Body                                                                                                                |
| ----------- | --------------------------------------------------------------------------------------------------------------------------- |
| 200         | Ok<br>{<br>    "adminFeeStatus": 1<br>}<br>if status is 0 : apply admin fees<br>if status is 1 or 2: don't apply admin fees |

## updatedoneinv/{doc_id}/{distr_id}/{store_id}/{doc_type}
**Verb:** POST
**Purpose:** updates some values in the columns corresponding to sales order
**DB Mapping:** updatedoneinv sproc
**URI Parameter:** doc_id, distr_id, store_id, doc_type
**Output:** 200-ok
## getBackOrderItemsNew/{distr_id}/{store_id}
**Verb:** GET
**Purpose:** queries db to get backorder items for each distr on each specific store.
**DB Mapping:** BACKORDER_ITEMS
**URI Parameter:** distr_id, store_id
**Output:** 

| Status Code | Message/Body                                                                                                                                                                                 |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 200         | Ok<br>With a list of the following object:<br>[<br>  {<br>    item_id:<br>	aname: <br>	doc_id:<br>	finalqty:<br>	ds_shipment:<br>	flag_type:<br>	gift_type:<br>	shipment_status:<br>  }<br>] |
| 404         | Not found - no special messasge                                                                                                                                                              |

## leaderverification/{leaderID}/{distrID}
**Verb:** GET
**Purpose:** verifies that if the distr is a leader of another distr
**DB Mapping:** LEADER_verification sproc
**URI Parameter:** leaderId, distr_id
**Output:** 200 - ok with message true or false
## memberid/{id}
**Verb:** GET
**Purpose:** get information of a specific user
**DB Mapping:** getmemberid sproc
**URI Parameter:** id = distr_id
**Output:**

| Status Code | Message/Body                                                                                                                                                                                                                       |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 200         | Ok with a list of <br>[<br>  {<br>    distr_id:<br>	service_center:<br>	aname:<br>	distr_ident:<br>	address:<br>	telephone:<br>	e_mail:<br>	area_id:<br>	area_aname: <br>	account_owner:<br>	account_num:<br>	tax_num:<br>  }<br>] |
| 404         | not found - no special message                                                                                                                                                                                                     |

## member_fees_verification/{distr_id}/{service_center}
**Verb:** GET
**Purpose:** verifies that a member has paid their membership fees
**DB Mapping:** MEMB_FEES_VRF sproc
**URI Parameter:** distr_id and service_center
**Output:** 
- 200 Ok
- 404 Not found
## deserve_bonus/{distr_id}
**Verb:** GET
**Purpose:** returns a list of the bonus deserved by a member.
**DB Mapping:** DESRV_BONUS sproc
**URI Parameter:** distr_id
**Output:**

| Code | Message                                                                                              |
| ---- | ---------------------------------------------------------------------------------------------------- |
| 200  | Ok and a body of the following obj<br>[<br>   {<br>      distr_id:<br>	  net_desrv:<br>   }<br>]<br> |
| 404  | Not found.                                                                                           |
## memregister-v2/{leaderId}/{ds_shipment_place}/{areaId_8k}/{spname}/{inv_type}/{store_id}
**Verb:** PUT
**Purpose:** Creates a new membership starting with code 99%
**DB Mapping:** AZ1, ap, aq, a9, aa
**URI Parameter:** leaderId, ds_shipment_place, areaId_8k, spname, inv_type, store_id
**Request Body:**    
**Output:** 

| Code | Message                                                                                                                                                                                                                                                                     |
| ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 201  | Created {id: newDistrId}<br>                                                                                                                                                                                                                                                |
| 409  | Conflict with the following messages:<br>- if ds_shipment_place is null or empty:<br>{<br>  errMsg = برجاء ادخال منطقة شحن<br>}<br>- if duplicate distr_ident:<br>{<br>  errMsg = الرقم القومي مكرر<br>}<br>- if duplicate phone:<br>{<br>  errMsg = رقم التيلفون مكرر<br>} |

## heldItemReport/{distrID}
**Verb:** GET
**Purpose:** Returns a list of all held items across all Credit stores.
**DB Mapping:** BACKORDER_AVAILABLE_ITEMS
**URI Parameter:** distr_id
**Output:**

| Code | Message                                                                                                                                                                                                                                                                                                                                                                           |
| ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 200  | Ok<br>Returns a list of the following object:<br>[<br>     {<br>        "FLAG_TYPE": "CR",<br>        "DOC_ID": "030647001594",<br>        "DS_SHIPMENT": "030647002128",<br>        "SHIPMENT_STATUS": "4",<br>        "ITEM_ID": "3442",<br>        "ANAME": "كلين منظف شامبو السجاد برغوة 660مل شكل جديد",<br>        "QTY": 1.0,<br>        "AVAILABILITY": "1"<br>    }<br>] |
| 404  | Not found.                                                                                                                                                                                                                                                                                                                                                                        |
## newmembers/{distrID}
**Verb:** GET
**Purpose:** returns a list of all newly registered member
**DB Mapping:** NEW_MEMBERS sproc
**URI Parameter:** distrid
**Output:**

| Code | Message/Body                                                                                                                                                             |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 200  | Ok. A list of the following object<br>[<br>  {<br>    distr_id:<br>	service_center:<br>	distr_name:<br>	area_name:<br>	telephone:<br>	per_bp:<br>	join_date:<br>  }<br>] |
| 404  | Not found                                                                                                                                                                |

## distrratio/{distrID}
**Verb:** GET
**Purpose:** gets the ratio of a distr
**DB Mapping:** DISTR_RATIO sproc
**URI Parameter:** distrid
**Output:**

| Code | Message/Body                                                                                                                                                             |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 200  | Ok. A list of the following object<br>[<br>  {<br>    distr_id:<br>	service_center:<br>	distr_name:<br>	area_name:<br>	telephone:<br>	per_bp:<br>	join_date:<br>  }<br>] |
| 404  | Not found                                                                                                                                                                |

## shipmentcompanies
**Verb:** GET
**Purpose:** queries db and returns a list of all shipment companies
**DB Mapping:** DSSC table
**URI Parameter:** NA
**Output:**

| Code | Response Message/Body                                                                                     |
| ---- | --------------------------------------------------------------------------------------------------------- |
| 200  | Ok. Returns a list of the following object:<br>[<br>  {<br>     ds_shipment_comp:<br>	 aname:<br>  }<br>] |

## get_all_shipment_places
**Verb:** GET
**Purpose:** queries the db and returns all distrs shipment places
**DB Mapping:** SHIPMENTPA table
**URI Parameter:** NA
**Output:**

| Code | Response Message/Body                                                                                       |
| ---- | ----------------------------------------------------------------------------------------------------------- |
| 200  | Ok. Returns a list of the following object:<br>[<br>  {<br>     spname:<br>	 ds_shipment_place:<br>  }<br>] |
## get_shipment_places_by_area_id/{areaID}
**Verb:** GET
**Purpose:** queries db and return info on all distrs shipment places by areaID
**DB Mapping:** SHIPMENTPA table
**URI Parameter:** areaId = area_id
**Output:**

| Code | Response Message/Body                                                                                       |
| ---- | ----------------------------------------------------------------------------------------------------------- |
| 200  | Ok. Returns a list of the following object:<br>[<br>  {<br>     spname:<br>	 ds_shipment_place:<br>  }<br>] |
## get_shipment_places_by_distr_id/{distrID}
**Verb:** GET
**Purpose:** queries db and returns all distrs shipment places by distr_id.
**DB Mapping:** DISTR_SHIPPL
**URI Parameter:** distrId
**Output:**

| Code | Response Message/Body                                                                                                                          |
| ---- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| 200  | Ok. Returns a list of the following object:<br>[<br>  {<br>     distr_id:<br>	 ds_shipment_place:<br>	 spname:<br>	 address_notes:<br>  }<br>] |
| 404  | not found                                                                                                                                      |
## add_new_distr_shipment_place/{store_id}
**Verb:** PUT
**Purpose:** creates a new address location
**DB Mapping:** DISTR_SHIPPL
**URI Parameter:** store_id
**Request Body:** 
```
{
    "DISTR_ID": "12345678",
    "DS_SHIPMENT_PLACE": "020099",
    "SPNAME": "INDONESIA TEST",
    "ADDRESS_NOTES": "123 test street"
}
```
**Output:**

| Code | Response Message                                                                                                                                                                          |
| ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 201  | Created. Returns the following:<br>{<br>    "RECORD_ID":"563",<br>    "DS_SHIPMENT":"110003000001",<br>    "SHIPMENT_PLACE_NAME":"القاهره",<br>    "ADDRESS_NOTES":"123 test, cairo"<br>} |

## delete_distr_shipment_place_record/{id}
**Verb:** DELETE .. Nonfunctional
**Purpose:**
**DB Mapping:**
**URI Parameter:**
**Output:**
## stock/{item_id}/{store_id}
**Verb:** GET
**Purpose:** gets the stock of an item
**DB Mapping:** liveStock
**URI Parameter:** item_id, store_id
**Output:**

| Code | Response Message/Body                                                                                        |
| ---- | ------------------------------------------------------------------------------------------------------------ |
| 200  | Ok. Returns a list of the following object:<br>[<br>  {<br>     itemid:<br>	 qty:<br>	 store_id:<br>  }<br>] |
| 404  | Not found                                                                                                    |
## getinvoicedetails/{doc_id}
**Verb:**
**Purpose:**
**DB Mapping:**
**URI Parameter:**
**Output:**
## getlateinvoices/{distr_id}
**Verb:**
**Purpose:**
**DB Mapping:**
**URI Parameter:**
**Output:**
## missingordamageditems/{distr_id}
**Verb:**
**Purpose:**
**DB Mapping:**
**URI Parameter:**
**Output:**
## userpending/{userID}
**Verb:**
**Purpose:**
**DB Mapping:**
**URI Parameter:**
**Output:**
```
[
    {
        "DOC_ID": "9900031134233",
        "SO_INV_TYPE": "CR",
        "DISTR_ID": "00000001",
        "DISTRNAME": "ماى واي",
        "COUNTER": "0001",
        "ITEM_ID": "4227",
        "ITEMNAME": "كريم سبرينج تفتيح و ترطيب للأيدى شديدة الجفاف بالزبادى",
        "QTY_REQ": 1.000,
        "UNIT_PRICE": 23100.000,
        "TOT_PRICE": 23100.000,
        "ITEM_BP": 8.0,
        "TOTAL_BP": 8.0,
        "DOC_DATE": "2025-05-10",
        "ADD_TIME": "15:19:16",
        "AREMARKS": "Test salesorder",
        "STORE_ID": "01",
        "ADELIVERY": "1/1",
        "CUST_ID": "0"
    },
    {
        "DOC_ID": "9900031134233",
        "SO_INV_TYPE": "CR",
        "DISTR_ID": "00000001",
        "DISTRNAME": "ماى واي",
        "COUNTER": "0002",
        "ITEM_ID": "90",
        "ITEMNAME": "مصاريف شحن",
        "QTY_REQ": 1.000,
        "UNIT_PRICE": 23100.000,
        "TOT_PRICE": 23100.000,
        "ITEM_BP": 8.0,
        "TOTAL_BP": 8.0,
        "DOC_DATE": "2025-05-10",
        "ADD_TIME": "15:19:16",
        "AREMARKS": "Test salesorder",
        "STORE_ID": "01",
        "ADELIVERY": "1/1",
        "CUST_ID": "0"
    }
]
```
## userinvoices/{userID}

### userinvoices-v2/{userId}
**Verb:** GET

**Purpose:** Gets a list of all invoices from created sales orders

**DB Mapping:** UserInvoices & userinvoices_lastday. v2 maps to USERINVOICES_SUMMARY table

**NOTE:** V2 only works on dev env. and that's the one that has the datatypes annotated below, since we're changing structure entirely, new version should read from userinvoices-v2.

**NOTE:** Userinvoices is updated on both production and development to display CUST_ID. 

**URI Parameter:** a string for distrid (ex: 00000001)
**Output:** 
```
[

    {

        "DOC_ID": "100007000016", 

        "FLAG_TYPE": "CR", 

        "DISTR": "00000001", 

        "DISTR_NAME": "ماى واي", 

        "COUNTER": "0003", 

        "ITEM_ID": "90", 

        "ITEM_NAME": "مصاريف شحن", 

        "PRICE": 23.0,

        "QTY": 1.0, 

        "NET_TOTAL": 23.0, 

        "ITEM_BP": 0.0, 

        "TOTAL_BP": 0.0, 

        "DOC_DATE": "2025-02-25,

        "DS_SHIPMENT": "100007000006",

        "SHIPMENT_STATUS": "0",

        "DLV_DATE": "0000-00-00",

        "COMP_NAME": "ماى واى",

        "REF_NO": "",-

        "STORE_ID": "01",

        "ADELIVERY": "25022320064184-04/01",

        "REF_NO_87": "25022320064184",

	"CUST_ID":"00000001" 

    },

    {

        "DOC_ID": "100007000016",

        "FLAG_TYPE": "CR",

        "DISTR": "00000001",

        "DISTR_NAME": "ماى واي",

        "COUNTER": "0004",

        "ITEM_ID": "91",

        "ITEM_NAME": "مصاريف إدارية",

        "PRICE": 6.0,

        "QTY": 1.0,

        "NET_TOTAL": 6.0,

        "ITEM_BP": 0.0,

        "TOTAL_BP": 0.0,

        "DOC_DATE": "2025-02-25",

        "DS_SHIPMENT": "100007000006",

        "SHIPMENT_STATUS": "0",

        "DLV_DATE": "0000-00-00",

        "COMP_NAME": "ماى واى",

        "REF_NO": "",

        "STORE_ID": "01",

        "ADELIVERY": "25022320064184-04/01",

        "REF_NO_87": "25022320064184",

	"CUST_ID":"00000001" 

    }
 ]
```
## getPendingPoints/{distr_id}
**Verb:**
**Purpose:**
**DB Mapping:**
**URI Parameter:**
**Output:**
## getPersonalPoints/{distr_id}
**Verb:**
**Purpose:**
**DB Mapping:**
**URI Parameter:**
**Output:**
## invoices/{id}
**Verb:**
**Purpose:**
**DB Mapping:**
**URI Parameter:**
**Output:**
## distrrepsummary/{distrID}
**Verb:**
**Purpose:**
**DB Mapping:**
**URI Parameter:**
**Output:**

## api/memregister-v3/{leaderId}/{ds_shipment_place}/{areaId_8k}/{spname}/{inv_type}/{store_id}

**Verb**: Put

**Purpose**: Creates a new AZ1 record with corresponding AP, AQ, A9, and AA. AZ1 has an email property field

**URI Parameter:** leaderId, ds_shipment_place, areaId_8k, spname, inv_type, store_id

**Request Body:**    

**Output:** 


| Code | Message                                                                                                                                                                                                                                                                     |
| ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 201  | Created {id: newDistrId}<br>                                                                                                                                                                                                                                                |
| 409  | Conflict with the following messages:<br>- if ds_shipment_place is null or empty:<br>{<br>  errMsg = برجاء ادخال منطقة شحن<br>}<br>- if duplicate distr_ident:<br>{<br>  errMsg = الرقم القومي مكرر<br>}<br>- if duplicate phone:<br>{<br>  errMsg = رقم التيلفون مكرر<br>} |
