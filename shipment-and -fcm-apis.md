# TOC
- [Shipment APIs](#shipment-apis)
    - [GET/api/get-8k](#getapiget-8k)
    - [GET/api/active-8k](#getapiactive-8k)
- [FCM](#fcm)
    - [POST/api/send-fcm-one](#postapisend-fcm-one)
    - [POST/api/send-fcm-multicast](#postapisend-fcm-multicast)
    - [POST/api/send-fcm-list](#postapisend-fcm-list)
# Shipment APIs
These apis get the active and inactive 8k entries. Each of the active 8k entries have the following:
- StoreID: Only one store ID serving the entire 8k region.
- ShipmentPlaces: Multiple shipment places that the store serves.
- Store Myway (01) aka (Cairo/Menofeya) shipment branch operates on area_id 01. Shipment branch has many ds_shipment_places that can start with '10%' or '54%'
## GET/api/get-8k
- Full api url: https://mywayegypt-api.azurewebsites.net/api/get-8k
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
## GET/api/active-8k
- Full api url: `https://mywayegypt-api.azurewebsites.net/api/active-8k`
- Method: Get
- URI Parameter: Null
- Function: queries egy_azure.dbo.shipmentpa then retrieves all 8k areas that a store operate on. Store 01 operates on shipment place range of : "10%" and "53%" cairo and menofeya  and correspond to area_id 01. This is where the mongodb.schema("areas") gets populated based upon, since it has the direct relation between area_id and ds_shipment_place. Refer to the this api : [get_all_shipment_places](https://github.com/aelnoweihy/Legacy-Doc/blob/main/README.md#get_all_shipment_places)
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

# FCM
## POST/api/send-fcm-one
- Full api url: http://159.65.87.196:6001/api/send-fcm-one
- Method: Post
- Function: Sends a text, text + image notification to a specific userid
- URI Parameter
- Sample input:
```json
{
  "memberId": "1",
  "title": "Hello user 1 - 2",
  "body": "hello postman with img 2",
  "image": "https://firebasestorage.googleapis.com/v0/b/mobile-coco-web-cms/o/NotificationImgs%2FWhatsApp%20Image%202025-08-18%20at%2019.22.29_c3a46799.png?alt=media&token=c7a331eb-a49e-47fc-bbcb-bea0fd5435f6"
}
```
- Notes: 
    - memberId property value is as it exists in firebase. 
## POST/api/send-fcm-multicast
- Full api url: http://159.65.87.196:6001/api/send-fcm-multicast
- Method: Post
- Function: Sends multiple users the same notification that can contain: text, text + image, or text + image + button
- URI Parameter: null
- Sample input:
```json
{
    "memberIds": [
        "22",
        "38",
        "1"
    ],
    "title": "This",
    "body": "body",
    "image": "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQUPIfiGgUML8G3ZqsNLHfaCnZK3I5g4tJabQ&s",
    "data": {
        "navigate": "true",
        "uri": "http://159.65.87.196:6001/docs/#/default/post_send_fcm_multicast",
        "action": "view doc"
    }
}
```
- Notes: the data object is where the button is defined with : 
    - navigate: true
    - uri: string for the rerouting url
    - action: button text
## POST/api/send-fcm-list
- Full api url: `http://159.65.87.196:6001/api/send-fcm-list`
- Method: Post
- Function: Sends an array of FCM messages, each object in the array relates to a specific user. A notification may be: text, text + image, text + image + button
- URI Parameter: Null
- Sample input:
```json
[{
  "memberId": "22",
  "title": "hello-03",
  "body": "body",
  "image": "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQUPIfiGgUML8G3ZqsNLHfaCnZK3I5g4tJabQ&s",
  "data": {
    "navigate": "true",
    "uri": "http://159.65.87.196:6001/docs/#/default/post_send_fcm_multicast",
    "action": "view doc"
  },
  "topic":"mytopic"
},
{
 "memberId": "1",
  "title": "hello-03",
  "body": "body",
  "image": "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQUPIfiGgUML8G3ZqsNLHfaCnZK3I5g4tJabQ&s",
  "data": {
    "navigate": "true",
    "uri": "http://159.65.87.196:6001/docs/#/default/post_send_fcm_multicast",
    "action": "view doc"
  },
  "topic":"mytopic"
}]
```
- Notes: 
    - The topic property is optional. 
    - The topic property refers to the channel a user may be subscribed to.
    - A topic is created through the client, and the client subscribes to a specific topic
