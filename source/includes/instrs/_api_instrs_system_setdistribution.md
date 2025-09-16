## SetDistribution

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Sets the distribution instruction for trading fees on a single instrument.

Each trade (and some other activities, such as withdrawals) may incur fees that are paid by the account to the Exchange or that are deducted by the Exchange from the proceeds of a trade. These fees accumulate in Account 1, the OMS Fee Account. Distributions control what proportions of these fees are shared between the Exchange and AlphaPoint.

To see all the existing distribution instructions for a specific instrument, use **GetDistributions.** 

### Request

```json
{
    "distributionId": 0,
    "distributionPrct": 0.0,
    "absolute": false,
    "account": 0,
    "orderType": 0,
    "instrumentId": 0,
    "omsId": 0
}
```

The values for *DistributionPrct* and *Absolute* work together.

| Key              | Value                                                        |
| ---------------- | ------------------------------------------------------------ |
| distributionId   | **integer.** The ID of this distribution. Leave this as 0 in the Request if you are creating a new distribution; the system will assign an ID to it. If you are changing a distribution, specify the *distributionId* you are changing. To see the IDs that the system has assigned, use **GetDistribution.** |
| distributionPrct | **real.** The percentage of the fee collected by the Exchange that then accrues to AlphaPoint. For example, if the Exchange collects $10 USD as fee for a trade, and the value of *DistributionPrct* is set to 10 (%), then AlphaPoint accrues $1 USD for that trade. Decimal values are permitted in this field. You can have a *DistributionPrct* of 0.05, for example. |
| absolute         | **Boolean.** If *true,* the value of *DistributionPrct* is interpreted as a fixed amount; if *false,* it is interpreted as a percentage. The default is *false.* In the previous example, if the Exchange collects $20 USD as a fee for a trade, *DistributionPrct* is set to 10, and *Absolute* is set to *true,* then $10 accrues to AlphaPoint for that trade rather than 10% (which would be $2.00). |
| account          | **integer.** The ID of the account where AlphaPoint accrues its percentage of fees. This is *not* one of the three default accounts (1 OMS Fee, 2 OMS Deposit, or 3 OMS Adapter). There is usually only one account set up for accrual on any given Exchange. |
| orderType        | **integer.** The type of order to which this distribution pertains. One of:<br />**0** Unknown<br />**1** All Order Types<br />**2** Market<br />**3** Limit<br />**4** StopMarket<br />**5** StopLimit<br />**6** TrailingStopMarket<br />**7** TrailingStopLimt<br />**8** BlockTrade |
| instrumentId     | **integer.** The ID of the instrument whose trades trigger the fee distribution. |
| omsId            | **integer.** The ID of the Order Management System on which the instrument trades. |

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
