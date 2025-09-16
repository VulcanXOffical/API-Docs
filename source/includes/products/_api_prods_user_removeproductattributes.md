## RemoveProductAttributes

**Category:** User<br />
**Permissions:** Operator, Company<br />
**Call Type:** Synchronous

Removes a single key-value pair that describes an attribute of a single product.

### Request

```json
{
    "OMSId": 1,
    "ProductId": 1,
    "KeyName": "key",
    "KeyValue": "value"
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| OMSId     | **integer.** The ID of the Order Management System on which the product is available. |
| ProductId | **integer.** The ID of the product whose key-value pair attribute will be removed. |
| KeyName   | **string.** The Key portion of the key-value pair attribute to be removed. |
| KeyValue  | **string.** The Value portion of the key-value pair attribute to be removed. |

### Response

```json
{
    "result": true,
    "errormsg": "",
    "errorcode": 0,
    "detail": ""
}
```
A successful response indicates only that the product attribute removal request was received by the server, not that a successful removal took place. To see if the product attribute was removed, use **GetProductAttributes.**

| Key    | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean**. A successful response returns *true*; an unsuccessful response (an error condition) returns *false*. |
| errormsg  | **string**. A successful response returns null; the *errormsg* parameter for an unsuccessful response returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer**. A successful response returns *0*. An unsuccessful response returns one of the errorcodes shown in the *errormsg* list. |
| detail    | **string**. Message text that the system may send. Usually *null*. |


