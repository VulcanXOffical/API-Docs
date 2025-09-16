## ResetTreasuryLimits

**Category:** System<br />**Permissions:** SUPERUSER<br />**Call Type:** Synchronous

Resets the treasury limits for the specific *accountID* and *assetId.* 

Internally, the AlphaPoint Exchange maintains collections in which are stored account statistics by product and instrument. The call **ResetTreasuryLimits** resets the account's *product* statistics.

### Request

```json
{
    "omsId": 0,
    "accountId": 0,
    "assetId": 0
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| omsId     | **integer.** The Order Management System on which the asset (product) and the account trade. |
| accountId | **integer.** The ID of the account whose treasury limits you want to reset. |
| assetId   | **integer.** The ID of the *product* whose treasury limits you want to reset for the specified account. In this explicit case, *assetId* = *productId.* |

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


