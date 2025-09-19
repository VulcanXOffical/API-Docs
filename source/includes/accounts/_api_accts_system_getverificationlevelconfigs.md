## GetVerificationLevelConfigs

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Returns all product configurations for all Verification Levels on a given Order Management System.

### Request

```json
{
    "OMSId": 1
}
```

| Key   | Value                                                        |
| ----- | ------------------------------------------------------------ |
| OMSId | **integer.** The ID of the Order Management System whose Verification Level information you want to return. |

### Response

```json
[
    {
        "level": 1,
        "omsId": 1,
        "products": [
            {
                "verificationLevel": 1,
                "omsId": 1,
                "productId": 1,
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
                "withdrawProcessingDelaySec": 0
            }
        ]
    }
]
```

The Response returns an array of Verification Levels, each of which consists of an array of product configurations at that level.

| Key                         | Value                                                        |
| --------------------------- | ------------------------------------------------------------ |
| level                       | **integer.** The Verification Level (usually 0 &ndash; 10, but can be operator-defined). |
| omsId                       | **integer.** The ID of the Order Management System where the products trade. |
| products                    | **array of JSON objects** See the following key-value pairs. |
| verificationLevel           | **integer.** The Verification Level for this product configuration. This value should match the value for *level* at the top of the Response object. |
| omsId                       | **integer.** The Order Management System on which this specific product trades. This value should match the value for *omsId* at the top of the Response object. |
| productId                   | **integer.** The ID of the product at this Verification Level. |
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
| depositTicketWorkflow       | **string.** A set of defined workflows for deposits, defined and named during the installation of the Exchange. Choices are:<br />**0** Internal<br />**1** External   |
| withdrawTicketWorkflow      | **string.** A set of defined workflows for deposits, defined and named during the installation of the Exchange. Choices are:<br />**0** Internal<br />**1** External |


