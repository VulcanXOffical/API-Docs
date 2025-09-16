## GetDistributions

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Returns the distribution instructions for a specific instrument.

Each trade (and some other activities, such as withdrawals) may incur fees that are paid by the account to the Exchange or that are deducted by the Exchange from the proceeds of a trade. These fees accumulate in Account 1, the OMS Fee Account. Distributions control what proportions of these fees are shared between the Exchange and AlphaPoint.

### Request

```json
{
    "OMSId": 1,
    "InstrumentId": 1
}
```

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| OMSId        | **integer.** The ID of the Order Management System where the instrument named in *InstrumentId* trades. |
| InstrumentId | **integer.** The ID of the instrument whose distributions will be returned. |

### Response

```json
[
    {
        "DistributionId": 1,
        "DistributionPrct": 0.0,
        "Absolute": false,
        "Account": 0,
        "OrderType": "Unknown",
        "InstrumentId": 0,
        "OMSId": 0
    },
]
```

The Response is an array of distributions, each element of the array is for a separate *OrderType* and *DistributionPrct.* The values for *DistributionPrct* and *Absolute* work together.

| Key              | Value                                                        |
| ---------------- | ------------------------------------------------------------ |
| DistributionId   | **integer.** The ID of this distribution.                    |
| DistributionPrct | **real.** The percentage of the fee collected by the Exchange that then accrues to AlphaPoint. For example, if the Exchange collects $10 USD as fee for a trade, and the value of *DistributionPrct* is set to 10 (%), then AlphaPoint accrues $1 USD for that trade. Decimal values are permitted in this field. You can have a *DistributionPrct* of 0.05, for example. |
| Absolute         | **Boolean.** If *true,* the value of *DistributionPrct* is interpreted as a fixed amount; if *false,* it is interpreted as a percentage. The default is *false.* In the previous example, if the Exchange collects $20 USD as a fee for a trade, *DistributionPrct* is set to 10, and *Absolute* is set to *true,* then $10 accrues to AlphaPoint for that trade rather than 10% (which would be $2.00). |
| Account          | **integer.** The ID of the account where AlphaPoint accrues its percentage of fees. This is *not* one of the three default accounts (1 OMS Fee, 2 OMS Deposit, or 3 OMS Adapter). There is usually only one account set up for accrual on any given Exchange. |
| OrderType        | **string.** The type of order to which this distribution pertains. One of:<br />Unknown<br />All Order Types<br />Market<br />Limit<br />StopMarket<br />StopLimit<br />TrailingStopMarket<br />TrailingStopLimt<br />BlockTrade |
| InstrumentId     | **integer.** The ID of the instrument whose trades trigger the fee distribution. |
| OMSId            | **integer.** The ID of the Order Management System on which the instrument trades. |


