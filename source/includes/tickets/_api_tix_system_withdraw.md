## Withdraw (DEPRECATED)

**Category:** System<br />**Permissions:** Operator, Withdraw<br />**Call Type:** Synchronous

Executes a withdrawal of a product. This call is no longer used and is documented here only for completeness. This call has been replaced by **CreateWithdrawTicket.**

### Request

```json
{
    "omsId": 0,
    "accountId": 0,
    "productId": 0,
    "amount": 0.0,
    "templateForm": "",
    "templateFormType": ""
}
```

| Key              | Value                                                        |
| ---------------- | ------------------------------------------------------------ |
| omsId            | **integer.** The ID of the Order Management System from which the withdrawal is to be made. |
| accountId        | **integer.** The ID of the account from which the withdrawal is to be made. |
| productId        | **integer.** The ID of the product (asset) being withdrawn.  |
| amount           | **real.** The unit and fractional quantity of the withdrawal; for example 2.5 BitCoin or 2018.17 US Dollars. |
| templateForm     | **object.** The contents of the template form vary from Account Provider to Account Provider, depending on the asset being withdraw and the identity of the Account Provider. |
| templateFormType | **string.** The name of the template being used for the withdrawal. Templates vary from Account Provider to Account Provider. |

### Response

```json
{
    "result": true,
    "errormsg": "Operation Not Supported",
    "errorcode": 106,
    "detail": ""
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean.** If the call has been successfully received by the Order Management System, returns *true,* otherwise returns *false.* |
| errormsg  | **string.** A successful receipt of the call returns *null.* The *errormsg* key for an unsuccessful call can return:<br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errocode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer.** A successful receipt of the call returns 0. An unsuccessful receipt of the call returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send.           |


