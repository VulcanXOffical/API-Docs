## CancelTransferFunds

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Cancels a previously requested transfer of funds.

Users with Trading permission can cancel funds transfers only for their own accounts; users with Operator permission can cancel funds transfers for any account.

### Request

```json
{
    "OMSId": 1,
    "AccountId": 1,
    "TransferId": 1
}
```

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| OMSId      | **integer.** The ID of the Order Management System on which the original transfer was made. |
| AccountId  | **integer.** The ID of the account that made the transfer.   |
| TransferId | **integer.** The ID of the transfer to be canceled. You can get a list of transfers and their IDs by account using **GetTransfers.** |

### Response

```json
{
    "result": true,
    "errormsg": "",
    "errorcode": 0,
    "detail": ""
}
```
The Response is a standard response object.

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean.** If the call has been successfully received by the Order Management System, *result* is *true;* otherwise it is *false.* |
| errormsg  | **string.** A successful receipt of the call returns *null.* The *errormsg* key for an unsuccessful call returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer.** A successful receipt of the call returns 0. An unsuccessful receipt of the call returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send.           |
