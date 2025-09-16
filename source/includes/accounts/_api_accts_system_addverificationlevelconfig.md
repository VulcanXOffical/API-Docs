## AddVerificationLevelConfig

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Allows an operator to define the limitations of an array of different products belonging to a single Verification Level.

### Request

```json
[
    {
        "level": 1,
        "omsId": 1,
        "products": [
            {
                "verificationLevel": 1,
                "omsId": 1,
                "productId":1,
                "productName": "Bitcoin",
                "autoWithdrawThreshold": 0.0,
                "dailyDepositLimit": 0.0,
                "monthlyDepositLimit": 0.0,
                "yearlyDepositLimit": 0.0,
                "yearlyDepositNotionalLimit": 0.0,
                "dailyWithdrawLimit": 0.0,
                "monthlyWithdrawLimit": 0.0,
		        "yearlyWithdrawLimit": 0.0,
                "yearlyWithdrawNotionalLimit": 0.0,
                "notionalProductId": 1,
                "overLimitRejected": false,
                "withdrawProcessingDelaySec": 0,
		        "depositTicketWorkflow": "",
		        "withdrawTicketWorkflow": ""
            }
        ]
    }
]
```

| Key                         | Value                                                        |
| --------------------------- | ------------------------------------------------------------ |
| level                       | **integer.** The Verification Level (usually 0 &ndash; 10, but can be operator-defined). |
| omsId                       | **integer.** The ID of the Order Management System where the products trade. |
| products                    | **array of JSON objects** See the following key-value pairs. |
| verificationLevel           | **integer.** The Verification Level for this product configuration. This value should match the value for *level* at the top of the Request. |
| omsId                       | **integer.** The Order Management System on which this specific product trades. This value should match the value for *omsId* at the top of the Request. |
| productId                   | **integer.** The ID of the product whose Verification Level configuration you're setting. |
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
| overLimitRejected           | **Boolean.** If *true* a deposit or withdrawal is automatically rejected if the account has reached the daily, monthly, or yearly limits. If *false* the deposit or withdrawal is not rejected. Typically, this value is *true* for fiat currencies and *false* for cryptocurrencies. |
| withdrawProcessingDelaySec  | **integer.** Sets the number of seconds that withdrawal processing is delayed before the withdrawal process commences. A type of float. Typically used for fiat currencies and not used for cryptocurrencies. |
| depositTicketWorkflow       | **string.** A set of defined workflows for deposits, defined and named during the installation of the Exchange. Choices are:<br />**0** Internal<br />**1** External  |
| withdrawTicketWorkflow      | **string.** A set of defined workflows for deposits, defined and named during the installation of the Exchange.  Choices are:<br />**0** Internal<br />**1** External   |

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




