## EditVerificationLevelConfig

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Edits the configuration of a single Verification Level for a single product.

### Request

```json
{
    "verificationLevel": 0,
    "omsId": 0,
    "productId": 0,
    "productName": null,
    "autoWithdrawThreshold": 0.0,
    "dailyDepositLimit": 0.0,
    "monthlyDepositLimit": 0.0,
    "yearlyDepositLimit": 0.0,
    "yearlyDepositNotionalLimit": 0.0,
    "dailyWithdrawLimit": 0.0,
    "monthlyWithdrawLimit": 0.0,
    "yearlyWithdrawLimit": 0.0,
    "yearlyWithdrawNotionalLimit": 0.0,
    "notionalProductId": 0
} 
```

| Key                         | Value                                                        |
| --------------------------- | ------------------------------------------------------------ |
| verificationLevel           | **integer.** The Verification Level for this product configuration. |
| omsId                       | **integer.** The Order Management System on which this specific product trades. |
| productId                   | **integer.** The ID of the product whose Verification Level configuration you're changing. |
| productName                 | **string.** The full name of the product (not the product's symbol). For example, "BitCoin." |
| autoWithdrawThreshold       | **real.** The amount of this product that can be withdrawn without admin approval at this Verification Level, expressed in units and fractions of the product (not dollar value). For example 2.5 BitCoin or $3528.25 US  Dollars. |
| dailyDepositLimit           | **real.** The amount of this product that can be deposited per day without admin approval at this Verification Level, expressed in units and fractions of the product (not dollar value). |
| monthlyDepositLimit         | **real.** The amount of this product that can be deposited per month without admin approval at this Verification Level, expressed in units and fractions of the product. |
| yearlyDepositLimit          | **real.** The amount of this product that can be deposited per year without admin approval at this Verification Level, expressed in units and fractions of the product. |
| yearlyDepositNotionalLimit  | **real.** In some jurisdictions, deposits of cryptocurrency must be conducted in terms of the local fiat currency. The *yearlyDepositNotionalLimit* is the value of *yearlyDepositLimit* expressed in local fiat currency. |
| dailyWithdrawLimit          | **real.** The amount of this product that can be withdrawn per day without admin approval at this Verification Level, expressed in units and fractions of the product. |
| monthlyWithdrawLimit        | **real.** The amount of this product that can be withdrawn per month without admin approval at this Verification Level, expressed in units and fractions of the product. |
| yearlyWithdrawLimit         | **real.** The amount of this product that can be withdrawn per year without admin approval at this Verification Level, expressed in units and fractions of the product. |
| yearlyWithdrawNotionalLimit | **real.** In some jurisdictions, withdrawals of cryptocurrency must be conducted in terms of the local fiat currency. The *yearlyWithdrawNotionalLimit* is the value of *yearlyWithdrawLimit* expressed in local fiat currency. |
| notionalProductId           | **integer.** The ID of the notional &mdash; local, fiat currency &mdash; in which deposits and withdrawals are conducted in some jurisdictions. |

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
