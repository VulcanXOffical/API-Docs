## TransferFunds

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Transfers funds between accounts.

Users with Trading permission can transfer funds only from a *SenderAccountId* with which they're associated; users with Operator permission can transfer funds from any account.

### Request

```json
{
    "OMSId": 1,
    "SenderAccountId": 1,
    "ProductId": 1,
    "Amount": 100.00,
    "Notes": "User-entered notes.",
    "ReceiverUserName": "UserName1"
}
```

The call **TransferFunds** moves funds from *SenderAccountId* to the default account of the user  identified by *ReceiverUserName.*

| Key              | Value                                                        |
| ---------------- | ------------------------------------------------------------ |
| OMSId            | **integer.** The ID of the Order Management System on which the transfer will be made. |
| SenderAccountId  | **integer.** The ID of the account from which funds will be transferred. |
| ProductId        | **integer.** The ID of the product in which funds will be transferred, for example, the ID for BitCoin or Ethereum or Dollars. |
| Amount           | **real.** The units and fractions of the product to be transferred (not the dollar value). |
| Notes            | **string.** Any notes entered by the originator of the transfer. |
| ReceiverUserName | **string.** The Exchange username whose default account will receive the transfer. The transfer can be made only to the default account of the receiver. |

### Response

```json
{
    "result": true,
    "errormsg": "",
    "errorcode": 0,
    "detail": "{\"TransferId\": 1}"
}
```
The Response is a standard response object.

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean.** If the call has been successfully received by the Order Management System, *result* is *true;* otherwise it is *false.* |
| errormsg  | **string.** A successful receipt of the call returns *null.* The *errormsg* key for an unsuccessful call returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer.** A successful receipt of the call returns 0. An unsuccessful receipt of the call returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send. Contains TransferId if successful.        |


