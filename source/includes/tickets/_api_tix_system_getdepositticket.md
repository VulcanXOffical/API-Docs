## GetDepositTicket

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Returns details about a single deposit ticket. A deposit ticket documents that a deposit was made or attempted.

### Request

```json
{
    "OMSId": 1,
    "AccountId": 1,
    "RequestCode": "Request Code GUID",
    "TicketId": 100000002
}
```

| Key         | Value                                                        |
| ----------- | ------------------------------------------------------------ |
| OMSId       | **integer.** The ID of the Order Management System on which the deposit ticket was created. |
| AccountId   | **integer.** The ID of the account into which the deposit was made. |
| RequestCode | **string.** A globally unique ID (GUID) that identifies this specific deposit. |
| TicketId    | **long integer.** The ID of the specific deposit ticket, as assigned by the system. |

### Response

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
| assetManagerId      | **integer.** The ID of the Asset Manager on which the deposit was made. |
| accountId           | **integer.** The ID of the account into which the deposit was made. |
| assetId             | **integer.** The ID of the asset (product) that was deposited. |
| assetName           | **string.** The short name of the asset (product) that was deposited, for example BTC for BitCoin or USD for US Dollars. |
| amount              | **real.** The unit and fractional amount of the asset that was deposited, for example 2.5 BitCoin or 2018.17 US Dollars. |
| omsId               | **integer.** The ID of the Order Management System on which the deposit was made. |
| requestCode         | **string.** A globally unique alphanumeric string (GUID) assigned by the system that identifies this specific deposit. |
| requestIP           | **string.** The IP address from which the deposit request was made. |
| requestUser         | **integer.** The user ID of the user who made the deposit request. |
| requestUserName     | **string.** The user name of the user who made the deposit request, for example, jsmith. |
| operatorId          | **integer.** The user ID of the operator who managed the deposit request. |
| status              | **integer.** The current status of this deposit ticket. Some of these statuses are valid only for cryptocurrency deposits; some are only valid for deposits of fiat (national) currency; others are used by AlphaPoint internally. Any of the statuses may appear on a deposit ticket.<br /><br />**Deposit ticket statuses**<br />**0** New (new ticket awaiting operator review)<br />**1** AdminProcessing (an admin is looking at the ticket)<br />**2** Accepted (an admin accepts the ticket)<br />**3** Rejected (admin rejects the ticket)<br />**4** SystemProcessing (automatic processing; an unlikely status for a deposit)<br />**5** FullyProcessed (the deposit has concluded)<br />**6** Failed (the deposit has failed for some reason)<br />**7** Pending (Account Provider has set status to pending)<br />**8** Confirmed (Account Provider confirms the deposit)<br />**9** AmlProcessing (anti-money-laundering process underway)<br />**10** AmlAccepted (anti-money-laundering process successful)<br />**11** AmlRejected (deposit did not stand up to anti-money-laundering process)<br />**12** AmlFailed (anti-money-laundering process failed/did not complete)<br />**13** LimitsAccepted (deposit meets limits for fiat or crypto asset)<br />**14** LimitsRejected (deposit does not meet limits for fiat or crypto asset) |
| feeAmt              | **real.** The fee assessed for making the deposit, if any. Deposit fees usually are assessed in the asset/product being deposited. |
| updatedByUser       | **integer.** The user ID of the last user to have updated the ticket (status, amount, etc.; this is usually an admin). |
| updatedByUserName   | **string.** The user name of the last user to have updated the ticket, for example, jsmith. |
| ticketNumber        | **long integer.** An ID number assigned by the system to identify the ticket (as opposed to identifying the deposit). |
| depositInfo         | **string.** A set of key-value pairs that holds information about the source of the funds being deposited. This information was entered when the deposit ticket was created, as required by the Account Provider. It can vary from Account Provider to Account Provider. |
| createdTimeStamp    | **string.** The date and time when the deposit ticket was created, in Microsoft Ticks format. All dates and times are UTC. |
| lastUpdateTimeStamp | **string.** The date and time when the deposit ticket last was updated &mdash; usually by an admin changing its status &mdash;  in Microsoft Ticks format. All dates and times are UTC. |
| comments            | **string.** Any comment appended to the deposit ticket.      |
| attachments         | **string.** Any attachment to the deposit ticket.            |


