## AddProductAttributes

**Category:** User<br />
**Permissions:** Operator, Company<br />
**Call Type:** Synchronous

Adds a single key-value pair product attribute to a product.

### Request

```json
{
    "OMSId": 1,
    "ProductId": 1,
    "KeyName": key,
    "KeyValue": "value"
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| OMSId     | **integer.** The ID of the Order Management System where the product is traded. |
| ProductId | **integer.** The ID of the product whose attributes are being set. |
| KeyName   | **string.** The key portion of the key-value pair attribute being set. |
| KeyValue  | **string.** The value portion of the key-value pair attribute being set. |

### Response

```json
{
    "result": true,
    "errormsg": "",
    "errorcode": 0,
    "detail": ""
}
```

The response shows that the system has received the request to add product attributes, not that the attributes have been added. To see if an attribute has successfully been added, use **GetProductAttributes.**

| Key    | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean.** A successful receipt of the request returns *true*; and unsuccessful receipt (an error condition) returns *false*. |
| errormsg  | **string.** A successful receipt of the request returns *null*; the *errormsg* parameter for an unsuccessful request returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer.** A successful receipt of the request returns 0. An unsuccessful receipt returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send. Usually *null*. |


