## AddProductAttributes

**Category:** Trading<br />
**Permissions:** Operator<br />
**Call Type:** Synchronous

Adds an attribute to a specific product.

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("AddProductAttributes", {
  OMSId: 1,
  ProductId: 1,
  KeyName: "AnotherKey",
  KeyValue: "AnotherValue",
});
```

```http
POST /AP/AddProductAttributes HTTP/1.1
Host: hostname goes here...
aptoken: d0260e4b-bf6e-4fcd-a8cd-ad1cb01f2235 //valid sessiontoken
Content-Type: application/json
Content-Length: 107

{
    "OMSId": 1,
    "ProductId": 1,
    "KeyName": "AnotherKey",
    "KeyValue": "AnotherValue"
}
```

| Key       | Value                                                                                 |
| --------- | ------------------------------------------------------------------------------------- |
| OMSId     | **integer** The Id of the OMS where the product belongs._required._                   |
| ProductId | **integer**. The Id of the product which you want to add an attribute for._required._ |
| KeyName   | **string** The product attribute keyname to be set._required._                        |
| KeyValue  | **string**. The product attirbute keyvalue to be set._required._                      |

### Response

```json
{
  "result": true,
  "errormsg": null,
  "errorcode": 0,
  "detail": null
}
```

| Key       | Value                                                                                                                                                                                                                                                                                                         |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result    | **Boolean**. A successful request returns true; and unsuccessful request (an error condition) returns false.                                                                                                                                                                                                  |
| errormsg  | **string**. A successful request returns null; the _errormsg_ parameter for an unsuccessful request returns one of the following messages: Not Authorized (errorcode 20), Invalid Request (errorcode 100), Operation Failed (errorcode 101), Server Error (errorcode 102), Resource Not Found (errorcode 104) |
| errorcode | **integer**. A successful request returns 0. An unsuccessful request returns one of the _errorcodes_ shown in the _errormsg_ list.                                                                                                                                                                            |
| detail    | **string**. Message text that the system may send. Usually _null_.                                                                                                                                                                                                                                            |
