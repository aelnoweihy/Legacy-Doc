1) Full api url: https://mywayegypt-api.azurewebsites.net/api/get-8k
- Method: Get
- URI Parameter: Null
- Function: queries azure.dbo.acc0118k and returns a list of area_id, ashort.
- Sample output:
 ```json
[
    {
        "AREA_ID": "00",
        "ASHORT": ""
    },
    {
        "AREA_ID": "01",
        "ASHORT": "مصر الجديدة"
    },
    {
        "AREA_ID": "02",
        "ASHORT": "مدينة نصر"
    }
]
  ```
2) Full api url: https://mywayegypt-api.azurewebsites.net/api/active-8k
- Methid: Get
- URI Parameter: Null
- Function: queries egy_azure.dbo.shipmentpa then retrieves all 8k areas that a store operate on. Store 01 operates on shipment place range of : "10%" and "53%" cairo and menofeya  and correspond to area_id 01
- Sample output:
```json
[
    {
        "AREA_ID": "01",
        "AREA_NAME": "مصر الجديدة"
    },
    {
        "AREA_ID": "11",
        "AREA_NAME": "الآسماعيلية"
    },
    {
        "AREA_ID": "12",
        "AREA_NAME": "بورسعيد"
    },
    {
        "AREA_ID": "13",
        "AREA_NAME": "السويس"
    }
]
```
