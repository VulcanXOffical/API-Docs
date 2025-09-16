## AddInstrumentAttributes

**Category:** User<br />
**Permissions:** Operator, Company<br />
**Call Type:** Synchronous

Adds a single key-value pair attribute to a specific instrument available on the exchange.

**TK** Would like a sample attribute that can be added to an instrument.

### Request

```json
{
    "OMSId": 1,
    "InstrumentId": 1,
    "KeyName": "key",
    "KeyValue": "value"
}
```

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| OMSId        | **integer.** The ID of the Order Management System on which the instrument is traded. |
| InstrumentId | **integer.** The ID of the instrument to which you are adding the attribute. |
| KeyName      | **string.** The key portion of the key-value pair that forms the attribute. |
| KeyValue     | **string.** The value portion of the key-value pair that forms the attribute. |

### Response

```json
{
    "result":true,
    "errormsg":"",
    "errorcode":0,
    "detail":""
}
```
A successful response indicates only that the instrument attribute add request was received by the server, not that a successful addition  took place. To see if the instrument  attribute was added, use **GetInstrumentAttributes.**

| Key    | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean**. A successful response returns *true*; an unsuccessful response (an error condition) returns *false*. |
| errormsg  | **string**. A successful response returns null; the *errormsg* parameter for an unsuccessful response returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104) |
| errorcode | **integer**. A successful response returns *0*. An unsuccessful response returns one of the errorcodes shown in the *errormsg* list. |
| detail    | **string**. Message text that the system may send. Usually *null*. |



