## GetAllAssetManagerWalletTickets

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Returns an array of all Asset Manager wallet tickets that meet the criteria set in the Request.

The Asset Manager wallet is a joint wallet for all Account Providers on the Exchange. Only a user with Operator permission may call **GetAllAssetManagerWalletTickets.**

### Request

```json
{
    "assetManagerId": 0,
    "accountProviderId": 0,
    "assetId": 0,
    "ticketId": "",
    "TicketType": 0,
    "TicketStatus": 0,
    "ticketNumber": 0,
    "assetManagerServiceId": "1",
    "startIndex": 0,
    "limit": 0
}
```

In the Request, some fields are optional so that **GetAllAssetManagerWalletTickets** can return tickets that meet specific criteria.

| Key                   | Value                                                        |
| --------------------- | ------------------------------------------------------------ |
| assetManagerId        | **integer.** The ID of the Asset Manager to which the wallet is linked. Different Order Management Systems may have different Asset Manager IDs. |
| accountProviderId     | **integer.** The ID of the Account Provider that is linked to the Asset Manager. |
| assetId               | **integer.** OPTIONAL The ID of the asset (product) on the exchange that caused the generation of the ticket. By setting the *assetId* value to 0, tickets for all assets are returned. |
| ticketId              | **string.** OPTIONAL A unique ID (alphanumeric) assigned by the system to the ticket. By leaving the *ticketId* value as *null* (empty string), tickets with any ID are returned. |
| ticketType        | **integer.** Describes the type of error or condition that triggered the ticket. One of:<br />**0** Unknown (an error condition)<br />**1** LowBalance<br />**2** HighBalance<br />**3** Transfer<br />**4** BalanceRequired<br />**5** BalanceMismatch<br />**6** WithdrawError<br />**7** DepositError<br />**8** AccountProviderError |
| ticketStatus      | **integer.** Describes the disposition of the ticket. One of:<br />**0** Unknown (an error condition)<br />**1** Open<br />**2** Resolved<br />**3** Rejected<br />**4** Notification |
| ticketNumber          | **integer.** OPTIONAL The number of this ticket on the exchange. A value of 0 for *ticketNumber* returns tickets with all numbers. |
| assetManagerServiceId | **string.** The *assetManagerServiceId* is an alphanumeric string pre-configured for the specific Exchange. For current installations, this value is "1". |
| startIndex            | **integer.** OPTIONAL The location in the series of Asset Manager wallet tickets at which to begin returning tickets. The most recent wallet ticket is 0; the count increments backwards. |
| limit                 | **integer.** OPTIONAL The count of Asset Manager wallet tickets to return (starting at *startIndex*). For example, a value of 100 returns 100 wallet tickets beginning with the ticket at position *startIndex.* A value of 0 returns only the most recent wallet ticket. |

### Response

```json
[
    {
        "assetManagerId": 0,
        "accountProviderId": 0,
        "assetId": 0,
        "ticketId": "",
        "lastUpdatedTime": 0,
        "lastUpdatedBy": 0,
        "ticketNumber": 0,
        "assetManagerServiceId": "1",
        "info": "",
        "TicketType": 0,
        "TicketStatus": 0
    }
]
```

The Response is an array of wallet tickets meeting the criteria set in the Request.

| Key                    | Value                                                        |
| ---------------------- | ------------------------------------------------------------ |
| assetManagerId         | **integer.** The ID of the Asset Manager to which the wallet is linked. |
| accountProviderId      | **integer.** The ID of the Account Provider that is linked to the Asset Manager. |
| assetId                | **integer.** The ID of the asset (product) to which the wallet ticket refers. |
| ticketId               | **string.** The unique ID (alphanumeric) assigned by the system to the ticket. |
| lastUpdatedTime        | **long integer.** The date and time stamp for the last time this wallet ticket was updated, in POSIX format. All dates and times are given as UTC. |
| lastUpdatedBy          | **integer.** The ID of the last user to update the wallet ticket (if any). Only a user with Operator permission can update an Asset Manager wallet ticket. |
| ticketNumber           | **integer.** The number of this ticket on the Exchange.      |
| assetManagerService Id | **string.** An alphanumeric string pre-configured for the specific Exchange. In current installations, always returns a value of "1". |
| info                   | **string.** Any message added to the wallet ticket by the system. |
| ticketType        | **integer.** Describes the type of error or condition that triggered the ticket. One of:<br />**0** Unknown (an error condition)<br />**1** LowBalance<br />**2** HighBalance<br />**3** Transfer<br />**4** BalanceRequired<br />**5** BalanceMismatch<br />**6** WithdrawError<br />**7** DepositError<br />**8** AccountProviderError |
| ticketStatus      | **integer.** Describes the disposition of the ticket. One of:<br />**0** Unknown (an error condition)<br />**1** Open<br />**2** Resolved<br />**3** Rejected<br />**4** Notification |
