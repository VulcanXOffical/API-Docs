## ReverseAccountHold

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Requests a hold be reversed for an account.

### Request

```json
{
    "omsId": 0,
    "accountId": 0,
    "assetId": 0,
    "transactionId": 0,
    "referenceId": 0,
    "TransactionReferenceType": 0
}
```

| Key                      | Value                                                        |
| ------------------------ | ------------------------------------------------------------ |
| omsId                    | **integer.** The ID of the Order Management System on which the account operates. |
| accountId                | **integer.** The ID of the account that has a hold on it that you want to reverse. |
| assetId                  | **integer** The ID of the asset (product) on which the hold is placed. |
| transactionId            | **long integer.** The ID of the underlying transaction. |
| referenceId              | **integer.**  The ID of the specific hold.    |
| TransactionReferenceType | **integer.** A number representing the type of action or event that triggered the transaction that caused the hold. One of:<br />**1** Trade<br />**2** Deposit<br />**3** Withdraw<br />**4** Transfer<br />**5** OrderHold<br />**6** WithdrawHold<br />**7** DepositHold<br />**8** MarginHold<br />**9** ManualHold<br />**10** ManualEntry<br />**11** MarginAcquisition<br />**12** MarginRelinquish<br />**13** MarginQuoteHold                                                |

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








