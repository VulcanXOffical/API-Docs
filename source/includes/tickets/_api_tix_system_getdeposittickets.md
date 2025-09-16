## GetDepositTickets

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Returns an array of deposit ticket objects for a specific account. The call returns *all* tickets for a given account. Use **GetDepositTicket** to return a single ticket. Operators (only) can use **GetAllDepositTickets** to return a subset of tickets.

Users with Trading permission can return deposit ticket information only for accounts with which they're associated; users with Operator permission can return deposit ticket information for any account.

### Request

```json
{
    "OMSId": 1,
    "OperatorId": 1,
    "AccountId": 1
}
```

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| OMSId      | **integer.** The ID of the Order Management System on which the account operates whose tickets you want to return. |
| OperatorId | **integer.** A user with Operator permission should put the Operator's ID here; a user with Trading permission should put the value 1 here. |
| AccountId  | **integer.** The account whose deposit tickets you want to return. |

### Response

```json
[
    {
        "assetManagerId": 0,
        "accountId": 0,
        "assetId": 0,
        "assetName": null,
        "amount": 0.0,
        "omsId": 0,
        "requestCode": "",
        "requestIP": "",
        "requestUser": 0,
        "requestUserName": "",
        "operatorId": 0,
        "Status": 0,
        "feeAmt": 0.0,
        "updatedByUser": 0,
        "updatedByUserName": "",
        "ticketNumber": 0,
        "depositInfo": null,
        "createdTimestamp": "0001-01-01T00:00:00",
        "lastUpdateTimeStamp": "0001-01-01T00:00:00",
        "comments": null,
        "attachments": null
    },
]
```
The Response returns an array of deposit ticket information.

| Key             | Value                                                        |
| --------------- | ------------------------------------------------------------ |
| assetManagerId  | **integer.** The ID of the Asset Manager module that handled the deposit. |
| accountId       | **integer.** The ID of the account into which the deposit was made. |
| assetId         | **integer.** The ID of the asset (product) deposited. This may be cryptocurrency or fiat (national) currency. |
| assetName       | **string.** The short name of the asset being deposited, for example USD (US Dollars), BTC (BitCoin), etc. |
| amount          | **real.** The unit quantity and fractional quantity of the asset being deposited. For example, 2.5 BitCoin or 2018.17 US Dollars. |
| omsId           | **integer.** The ID of the Order Management System through which the asset was deposited. |
| requestCode     | **string.** A globally unique ID (GUID) that identifies the deposit ticket on the Exchange. |
| requestIP       | **string.** The IP address from which the deposit was received, for example 127.0.0.1. |
| requestUser     | **integer.** The user ID of the user making the deposit.     |
| requestUserName | **string.** The user name of the user making the deposit, for example, *jsmith.* |
| operatorId      | **integer.** The user ID of the human admin (operator) who accepted, rejected or placed the ticket in the Pending status. Operators set the status of fiat currency deposits; cryptocurrency deposits are handled automatically. |
| Status              | **integer.** The current status of the deposit ticket. Some of these statuses are valid only for cryptocurrency deposits and some are valid for fiat currency deposits.  Some of these statuses are used by AlphaPoint internally, yet they may appear on returned Deposit Ticket information.<br /><br />**Deposit ticket statuses:**<br />**0** New (new ticket awaiting operator review)<br />**1** AdminProcessing (An admin is looking at the ticket)<br />**2** Accepted (An admin accepts the ticket)<br />**3** Rejected (Admin rejects the ticket)<br />**4** SystemProcessing (automatic processing; an unlikely status for a deposit)<br />**5** FullyProcessed (the deposit has concluded)<br />**6** Failed (the deposit failed for some reason)<br />**7** Pending (Account Provider has set status to pending)<br />**8** Confirmed (Account Provider confirms the deposit)<br />**9** AmlProcessing (anti-money-laundering process underway)<br />**10** AmlAccepted (anti-money-laundering process successful)<br />**11** AmlRejected (deposit did not stand up to anti-money-laundering process)<br />**12** AmlFailed (anti-money-laundering process failed/did not complete)<br />**13** LimitsAccepted (deposit meets limits for fiat or crypto asset)<br />**14** LimitsRejected (deposit does not meet limits for fiat or crypto asset) |
| feeAmt | **real.** The fee assessed by the Exchange for making the deposit, if any. Such a fee normally is assessed in the asset being deposited. |
| updatedByUser | **integer.** The user ID of the person who made the most recent update to the deposit ticket. This user should be an admin (Operator). |
| updatedByUserName | **string.** The user name of the person (admin/Operator) who made the most recent update to the deposit ticket. |
| ticketNumber | **integer.** Number of the ticket on the Exchange. |
| depositInfo | **object.** A set of key-value pairs that holds information about the source of funds being deposited. This information was entered when the deposit ticket was created, as required by the Account Provider. It can vary from Account Provider to Account Provider. |
| createdTimeStamp | **string.** The date and time that the deposit ticket was created, in Microsoft Ticks format. All dates and times are UTC. |
| lastupdateTimeStamp | **string.** The date and time stamp that the deposit ticket last was updated, in Microsoft Ticks format. All dates and times are UTC. |
| comments | **string.** Any comment appended to the deposit ticket. |
| attachments | **string.** Any attachment to the deposit ticket. |




