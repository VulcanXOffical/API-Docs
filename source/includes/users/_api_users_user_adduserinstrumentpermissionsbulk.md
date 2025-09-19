## AddUserInstrumentPermissionsBulk

**Category:** User<br />**Permissions:** Operator, Company<br />**Call Type:** Synchronous

Adds permissions for multiple users to multiple instruments in a batch.

### Request

```json
{
    "OMSId": 1,
    "InstrumentIds": [1,2]
    "UserId": [1,2]
}
```

The set of instrument IDs are granted as permission to trade to the set of user IDs.

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| OMSId        | **integer.** The ID of the Order Management System on which the users operate and the instruments are traded. |
| InstrumentIds | **integer array.** A comma-separated array of the IDs of multiple instruments whose permission to trade is being granted to the list of users. |
| UserId       | **integer array.** A comma-separated array of the ID of the multiple users who are being granted permission to trade in the list of instruments. |

### Response

```json
{
    "result": "true",
    "errormsg": "",
    "errorcode": 0,
 }
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean.** If *true*, the permission change was received by the server; if *false*, the permission change was not received by the server. A result of *true* does not mean that the permissions have been changed, only that they were received. |
| errormsg  | **string.** A successful receipt of the quote returns null; the *errormsg* parameter for an unsuccessful receipt returns one of the following messages:<br/>Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer.** A successful receipt returns 0. An unsuccessful receipt returns on of the *errorcodes* shown in the *errormsg* list. |

