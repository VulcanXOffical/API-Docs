## RemoveUserInstrumentPermissions

**Category:** User<br />**Permissions:** Operator, Company<br />**Call Type:** Synchronous

Removes a single instrument permission (permission to trade that instrument) from a single user.

### Request

```json
{
    "OMSId": 1,
    "InstrumentId": 1,
    "UserId": 1
}
```

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| OMSId        | **integer.** The ID of the Order Management System on which the instrument trades and the user operates. |
| InstrumentId | **Integer.** The ID of the instrument whose permission to trade is being removed. |
| UserId       | **integer.** The ID of the user whose permission to trade in the instrument is being removed. |

### Response

```json
{
    "result":true,
    "errormsg":"",
    "errorcode":0,
    "detail":""
}
```

A successful response means that the server has received the request to remove the instrument permission, not that the instrument permission has been removed. To see if the instrument permission has been removed, use **GetAllUserInstrumentPermissions.**

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean**. A successful response returns *true*; an unsuccessful response (an error condition) returns *false*. |
| errormsg  | **string**. A successful response returns null; the *errormsg* parameter for an unsuccessful receipt returns one of the following messages: <br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104) |
| errorcode | **integer**. A successful receipt returns *0*. An unsuccessful receipt returns one of the errorcodes shown in the *errormsg* list. |
| detail    | **string**. Message text that the system may send. Usually *null*. |
