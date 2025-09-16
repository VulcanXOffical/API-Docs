## GetAllDepositTickets

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Returns an array of all deposit tickets on the specified Order Management System. All deposit tickets from all accounts and all users are returned from the start of the Exchange to the present, subject only to the restrictions set by the *StartIndex* and *Limit* values.

Only a user with Operator permission can issue **GetAllDepositTickets.**

### Request

```json
{
    "OMSId": 1,
    "OperatorId": 1,
    "StartIndex": 0,
    "Limit": 0,
    "IncludeComments": true
}
```

The values for *OMSId* and *OperatorId* are required; the key-value pairs *StartIndex* and *Limit* are optional. You can include *StartIndex*, *Limit,* or both.

| Key            | Value                                                        |
| -------------- | ------------------------------------------------------------ |
| OMSId          | **integer.** REQUIRED The ID of the Order Management System on which the deposit tickets were created. |
| OperatorId     | **integer.** REQUIRED The user ID of the user with Operator permission who is issuing the **GetAllDepositTickets** call. |
| StartIndex     | **integer.** OPTIONAL The earliest location in the series of deposit tickets at which to begin returning tickets. Tickets are returned from that location forward (that is, from then toward now). The most recent deposit ticket is ticket 0. If you do not include a *StartIndex* key and value in your request, tickets from the beginning of the Exchange will be returned (subject to *Limit.*) |
| Limit          | **integer.** OPTIONAL The count of deposit tickets you want returned. For example, if you set the value of *Limit* to 50, a maximum of 50 deposit tickets will be returned. That maximum may be further restricted by the position of *StartIndex.* For example, if your *StartIndex* is only ten tickets back, and you include a *Limit* value of 50, you're still only going to get ten tickets. |
| IncludeComments | **Boolean.** OPTIONAL Include or exclude ticket comments in 'Comments' field of each ticket in response. Useful for performance reasons. |

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
        "depositInfo": {
        	"Full Name": "John Smith",
        	"language": "en",
        	"Bank Name": "Rubber City Bank"
    		},
        "createdTimestamp": "0001-01-01T00:00:00",
        "lastUpdateTimeStamp": "0001-01-01T00:00:00",
        "comments": null,
        "attachments": null
    },
]
```

The Response returns an array of deposit tickets matching the criteria set in the Request.

| Key             | Value                                                        |
| --------------- | ------------------------------------------------------------ |
| assetManagerId  | **integer.** The ID of the Asset Manager module that handled the deposit. |
| accountId       | **integer.** The ID of the account into which the deposit was made. |
| assetId         | **integer.** The ID of the asset (product) deposited. This may be cryptocurrency or fiat (national) currency. |
| assetName       | **string.** The short name of the asset being deposited, for example USD (US Dollars), BTC (BitCoin), etc. |
| amount          | **real.** The unit quantity of asset being deposited. For example, 2.5 BitCoin or 2018.17 US Dollars. |
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


