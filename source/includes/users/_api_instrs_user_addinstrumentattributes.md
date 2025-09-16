## AddInstrumentAttributes

**Category:** User<br />
**Permissions:** Operator, Company<br />
**Call Type:** Synchronous

Adds a single key-value pair attribute to a specific instrument available on the exchange.

### Request

```json
{
  "OMSId": 1,
  "InstrumentId": 1,
  "KeyName": "key",
  "KeyValue": "value"
}
```

| Key          | Value                                                                                 |
| ------------ | ------------------------------------------------------------------------------------- |
| OMSId        | **integer.** The ID of the Order Management System on which the instrument is traded. |
| InstrumentId | **integer.** The ID of the instrument to which you are adding the attribute.          |
| KeyName      | **string.** The key portion of the key-value pair that forms the attribute.           |
| KeyValue     | **string.** The value portion of the key-value pair that forms the attribute.         |

### Response

```json
{
  "result": true,
  "errormsg": "",
  "errorcode": 0,
  "detail": ""
}
```

A successful response indicates only that the instrument attribute add request was received by the server, not that a successful addition took place. To see if the instrument attribute was added, use **GetInstrumentAttributes.**

| Key       | Value                                                                                                                                                                                                                                                                                                                                 |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result    | **Boolean**. A successful response returns _true_; an unsuccessful response (an error condition) returns _false_.                                                                                                                                                                                                                     |
| errormsg  | **string**. A successful response returns null; the _errormsg_ parameter for an unsuccessful response returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104) |
| errorcode | **integer**. A successful response returns _0_. An unsuccessful response returns one of the errorcodes shown in the _errormsg_ list.                                                                                                                                                                                                  |
| detail    | **string**. Message text that the system may send. Usually _null_.                                                                                                                                                                                                                                                                    |
