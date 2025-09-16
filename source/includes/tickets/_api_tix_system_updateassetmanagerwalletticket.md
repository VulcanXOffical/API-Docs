## UpdateAssetManagerWalletTicket

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Changes the data in, and updates, a single Asset Manager wallet ticket.

Only a user with Operator permission can update an Asset Manager wallet ticket.

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

| Key                    | Value                                                        |
| ---------------------- | ------------------------------------------------------------ |
| assetManagerId         | **integer.** The ID of the Asset Manager to which the wallet is linked. Different Order Management Systems may have different Asset Manager IDs. |
| accountProviderId      | **integer.** The ID of the Account Provider that is linked to the Asset Manager. |
| assetId                | **integer.** The ID of the asset (product) of the Exchange that caused the generation of a ticket. |
| ticketId               | **string.** A GUID (alphanumeric) assigned by the system to the ticket. |
| ticketType        | **integer.** Describes the type of error or condition that triggered the ticket. One of:<br />**0** Unknown (an error condition)<br />**1** LowBalance<br />**2** HighBalance<br />**3** Transfer<br />**4** BalanceRequired<br />**5** BalanceMismatch<br />**6** WithdrawError<br />**7** DepositError<br />**8** AccountProviderError |
| ticketStatus      | **integer.** Describes the disposition of the ticket. One of:<br />**0** Unknown (an error condition)<br />**1** Open<br />**2** Resolved<br />**3** Rejected<br />**4** Notification |
| ticketNumber           | **integer.** The number of this ticket on the Exchange.      |
| assetManagerService Id | **string.** The *assetManagerServiceId* is an alphanumeric string pre-configured for the specific Exchange. For current installations, this value is "1". |
| startIndex             | **integer.** The **UpdateAssetManagerWalletTicket** call ignores the value for *startIndex*. You can safely set this value to 0. |
| limit                  | **integer.** The **UpdateAssetManagerWalletTicket** call ignores the value for *limit.* You can safely set this value to 0. |

### Response


```json
{
    "accountProviderId": 0,
    "assetId": 0,
    "ticketType": 0,
    "ticketStatus": 0,
    "ticketId": null,
    "ticketNumber": 0
}
```

| Key               | Value                                                        |
| ----------------- | ------------------------------------------------------------ |
| accountProviderId | **integer.** The ID of the Account Provider associated with the creation of the ticket (for example, the error condition that the ticket represents). |
| assetId           | **integer.** The ID of the asset associated with the ticket. |
| ticketType        | **integer.** Describes the type of error or condition that triggered the ticket. One of:<br />**0** Unknown (an error condition)<br />**1** LowBalance<br />**2** HighBalance<br />**3** Transfer<br />**4** BalanceRequired<br />**5** BalanceMismatch<br />**6** WithdrawError<br />**7** DepositError<br />**8** AccountProviderError |
| ticketStatus      | **integer.** Describes the disposition of the ticket. One of:<br />**0** Unknown (an error condition)<br />**1** Open<br />**2** Resolved<br />**3** Rejected<br />**4** Notification |
| ticketId          | **string.** The unique ID (alphanumeric) assigned by the system to the ticket. |
| ticketNumber      | **integer.** The number of this ticket on the exchange.      |


