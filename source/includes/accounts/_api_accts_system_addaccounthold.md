## AddAccountHold

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Places a *manual* hold on an account for a specified amount of a specified asset. A hold occurs automatically when a deposit or withdrawal is over the threshold limit set for the account by its Verification Level.

### Request

```json
{
    "omsId": 0,
    "accountId": 0,
    "assetId": 0,
    "amount": 0.0
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| omsId     | **integer.** The ID of the Order Management System on which the account operates. |
| accountId | **integer.** The ID of the account on which the hold is being placed. |
| assetId   | **integer.** The ID of the asset on which the hold is placed, for example US Dollars or BitCoin. |
| amount    | **real.** The quantity of the asset that is placed on hold, for example 2.5 BitCoin or $2018.12 dollars. |

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



