## RemoveInstrumentAttributes

**Category:** User<br />**Permissions:** Operator, Company<br />**Call Type:** Synchronous

Removes a single attribute key-value pair from an instrument.

### Request

```json
{
    "OMSId": 1,
    "InstrumentId": 1,
    "KeyName": "key"
}
```

There is no need to specify the value of the attribute name.

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| OMSId        | **integer.** The ID of the Order Management System where the instrument is available. |
| InstrumentId | **integer.** The ID of the instrument whose attribute you want to remove. |
| KeyName      | **string.** The name portion of the key-value attribute you want to remove. |

### Response

```json
{
    "result":true,
    "errormsg":"",
    "errorcode":0,
    "detail":""
}
```
A successful response indicates only that the instrument attribute remove request was received by the server, not that a successful removal  took place. To see if the instrument  attribute was removed, use **GetInstrumentAttributes.**

| Key    | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean**. A successful response returns *true*; an unsuccessful response (an error condition) returns *false*. |
| errormsg  | **string**. A successful response returns null; the *errormsg* parameter for an unsuccessful response returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104) |
| errorcode | **integer**. A successful response returns *0*. An unsuccessful response returns one of the errorcodes shown in the *errormsg* list. |
| detail    | **string**. Message text that the system may send. Usually *null*. |

