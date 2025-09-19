## GetProductAttributes

**Category:** Trading<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

Get attributes of a specific product.

### Request

```javascript
const { APEX } = require("VulcanX-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("GetProductAttributes", {
  OMSId: 1,
  ProductId: 1,
});
```

```http
POST /AP/GetProductAttributes HTTP/1.1
Host: hostname goes here...
aptoken: d0260e4b-bf6e-4fcd-a8cd-ad1cb01f2235 //valid sessiontoken
Content-Type: application/json
Content-Length: 44

{
    "OMSId": 1,
    "ProductId": 1
}
```

| Key       | Value                                                                              |
| --------- | ---------------------------------------------------------------------------------- |
| OMSId     | **integer** The Id of the OMS where the product belongs._required._                |
| ProductId | **integer**. The Id of the product which you want to get attributes of._required._ |

### Response

```json
[
  {
    "OMSId": 1,
    "ProductId": 1,
    "KeyName": "Pegged",
    "KeyValue": "true"
  }
]
```

The response is an array of objects, each object represents an product attribute in key-value pair.

| Key       | Value                                                           |
| --------- | --------------------------------------------------------------- |
| OMSId     | **integer**. Id of the OMS where the product belongs.           |
| ProductId | **integer**. Id of the product whose attribute/s were returned. |
| KeyName   | **string**. The product attribute keyname.                      |
| KeyValue  | **string**. The product attribute keyvalue.                     |
