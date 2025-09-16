## Deposit (DEPRECATED)

**Category:** System<br />**Permission:** SUPERUSER<br />**Call Type:** Synchronous

Deposits funds into an account. This call is no longer used and is documented here only for completeness. This call has been replaced by **CreateDepositTicket.** 

### Request

```json
{
    "omsId": 0,
    "accountId": 0,
    "instrumentId": 0,
    "amount": 0.0,
    "depositInfo": null
}
```

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| omsId        | **integer.** The ID of the Order Management System into which the deposit is being made. |
| accountId    | **integer.** The ID of the account receiving the deposit.    |
| instrumentId | **integer.** The ID of the product (not instrument) being deposited. The AlphaPoint exchange differentiates between products and instruments (two products comprise an instrument, BitCoin and dollars, for example).      |
| amount       | **real.** The unit and fractional amount of the deposit. For example, 2.5 BitCoin or 201.85 dollars. |
| depositInfo  | **JSON string object.** A JSON object describing a deposit form template. The template may vary from Account Provider to Account Provider. You can obtain a list of templates available to you (and their contents) by calling **GetDepositRequestInfoTemplate** (you must have Operator or Trading permissions). |

### Response

```json
{
    "result": true,
    "errormsg": "",
    "errorcode": 0,
    "detail": ""
}
```
| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean.** If the call has been successfully received by the Order Management System, *result* is *true;* otherwise it is *false.* |
| errormsg  | **string.** A successful receipt of the call returns *null.* The *errormsg* key for an unsuccessful call returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer.** A successful receipt of the call returns 0. An unsuccessful receipt of the call returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send.           |


