## UpdateDepositTicket

**Category:** System<br />**Permission:** Operator<br />**Call Type:** Synchronous

Updates the details of a deposit ticket for deposits of fiat currency (non-crypto national currencies, for example).

### Request

```json
{
    "assetManagerId": 0,
    "accountId": 0,
    "assetId": 0,
    "assetName": null,
    "amount": 0.0,
    "omsId": 0,
    "requestCode": null,
    "requestIP": null,
    "requestUser": 0,
    "requestUserName": null,
    "operatorId": 0,
    "Status": 0,
    "feeAmt": 0.0,
    "updatedByUser": 0,
    "updatedByUserName": null,
    "ticketNumber": 0,
    "depositInfo": null,
    "createdTimestamp": "0001-01-01T00:00:00",
    "lastUpdateTimeStamp": "0001-01-01T00:00:00",
    "comments": null,
    "attachments": null
}
```

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| assetManagerId      | **integer.** The ID of the system's asset manager module, usually 1. |
| accountId           | **integer.** The account receiving the deposit.              |
| assetId             | **integer.** The ID of the asset being deposited. An asset is functionally the same as a product; you can obtain a list of products/assets available on the Exchange by using **GetProducts.** |
| assetName           | **string.** The short name of the asset being deposited. For example, USD (US Dollars) or BTC (BitCoin). |
| amount              | **real.** The quantity of the asset being deposited. This is not the monetary value of the asset. For example, 2.5 BitCoins is 2.5. |
| omsId               | **integer.** The ID of the Order Management System where the deposit is being made, usually 1. |
| requestCode         | **string.** A *requestCode* is a globally unique ID assigned by the system. It identifies the deposit (as opposed to the deposit *ticket*). |
| requestIp           | **string.** The IP address from which the calling user made the deposit ticket request. |
| requestUser         | **integer.** The user ID of the user making the deposit ticket request. |
| requestUserName     | **string.** The user name of the user making the deposit ticket request, for example, jsmith. |
| operatorId          | **integer.** The ID of the trading venue operator. A deposit ticket can be updated only by a user with Operator permission. |
| status              | **integer.** The current status of this deposit ticket. Some of these statuses are valid only for cryptocurrency deposits; some are only valid for deposits of fiat (national) currency; others are used by AlphaPoint internally. Any of the statuses may appear on a deposit ticket.<br /><br />**Deposit ticket statuses**<br />**0** New (new ticket awaiting operator review)<br />**1** AdminProcessing (an admin is looking at the ticket)<br />**2** Accepted (an admin accepts the ticket)<br />**3** Rejected (admin rejects the ticket)<br />**4** SystemProcessing (automatic processing; an unlikely status for a deposit)<br />**5** FullyProcessed (the deposit has concluded)<br />**6** Failed (the deposit has failed for some reason)<br />**7** Pending (Account Provider has set status to pending)<br />**8** Confirmed (Account Provider confirms the deposit)<br />**9** AmlProcessing (anti-money-laundering process underway)<br />**10** AmlAccepted (anti-money-laundering process successful)<br />**11** AmlRejected (deposit did not stand up to anti-money-laundering process)<br />**12** AmlFailed (anti-money-laundering process failed/did not complete)<br />**13** LimitsAccepted (deposit meets limits for fiat or crypto asset)<br />**14** LimitsRejected (deposit does not meet limits for fiat or crypto asset) |
| feeAmt              | **real.** The amount of any fee for the deposit.             |
| updatedByUser       | **integer.** Contains the user ID of the user who updates the ticket. |
| updatedByUserName   | **string.** Contains the name of the user who updates the ticket. |
| ticketNumber        | **long integer.** A number assigned by the system to identify the ticket (as opposed to identifying the deposit). |
| depositInfo         | **object.** A set of key-value pairs that holds information about the source of the funds being deposited. This information was entered when the deposit ticket was created, as required by the Account Provider. It can vary from Account Provider to Account Provider. |
| createdTimeStamp    | **string.** The time and date stamp for when the deposit ticket was created, in Microsoft Ticks format. All time and date stamps are given as UTC. |
| lastUpdateTimeStamp | **string.** The time and date stamp for the last update to the deposit ticket after it was created. |
| comments            | **string.** Any comments appended to the deposit ticket.     |
| attachments         | **string.** Any attachments appended to the deposit ticket.  |
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

