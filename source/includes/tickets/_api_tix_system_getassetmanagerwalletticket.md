## GetAssetManagerWalletTicket

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Returns the details about a single specific Asset Manager wallet ticket. The key-value pairs in the Request identify the ticket to return.

### Request

```json
{
    "assetManagerId": 0,
    "accountProviderId": 0,
    "assetId": 0,
    "TicketType": 0,
    "TicketStatus": 0,
    "ticketId": "",
    "ticketNumber": 0,
    "assetManagerServiceId": "1",
    "startIndex": 0,
    "limit": 0
}
```

| Key                   | Value                                                        |
| --------------------- | ------------------------------------------------------------ |
| assetManagerId        | **integer.** The ID of the Asset Manager to which the wallet is linked. Different Order Management Systems may have different Asset Managers. |
| accountProviderId     | **integer.** The ID of the Account Provider that is linked to the Asset Manager for the asset identified in *assetId.* |
| assetId               | **integer.** The ID of the asset (product) of the Exchange that caused the generation of a ticket. |
| ticketType        | **integer.** Describes the type of error or condition that triggered the ticket. One of:<br />**0** Unknown (an error condition)<br />**1** LowBalance<br />**2** HighBalance<br />**3** Transfer<br />**4** BalanceRequired<br />**5** BalanceMismatch<br />**6** WithdrawError<br />**7** DepositError<br />**8** AccountProviderError |
| ticketStatus      | **integer.** Describes the disposition of the ticket. One of:<br />**0** Unknown (an error condition)<br />**1** Open<br />**2** Resolved<br />**3** Rejected<br />**4** Notification |
| ticketId              | **string.** A unique ID (alphanumeric) assigned by the system to the ticket. |
| ticketNumber          | **integer.** The number of this ticket on the Exchange.      |
| assetManagerServiceId | **string.** The *assetManagerServiceId* is an alphanumeric string pre-configured for the specific Exchange. For current installations, this value is "1". |
| startIndex            | **integer.** OPTIONAL The earliest location in the series of Asset Manager Wallet Tickets to begin searching for the one ticket you want returned. Tickets are searched from that location forward (that is, from then toward now, or from the past to the present). The most recent Asset Manager Wallet Ticket is ticket 0. Without a *startIndex* value, the system begins searching with the first Asset Manager Wallet Ticket on the Exchange. |
| limit                 | **integer.** OPTIONAL The count of Asset Manager Wallet Tickets to search. For example, if you set *limit* to 50, the Exchange begins searching at *startIndex* and looks at the next 50 tickets (moving from the ticket identified by *startIndex* towards the 0th &mdash; most recent &mdash; ticket). Once 50 tickets have been searched (in this case), the search ceases and either the specified ticket is returned or no ticket is returned. |

### Response

```json
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
```

The response is a single Asset Manager Wallet Ticket. Depending on values you set for *startIndex* and *limit*, **GetAssetManagerWalletTicket** may return no ticket.

| Key                   | Value                                                        |
| --------------------- | ------------------------------------------------------------ |
| assetManagerId        | **integer.** The ID of the Asset Manager to which the wallet is linked. |
| accountProviderId     | **integer.** The ID of the Account Provider that is linked to the Asset Manager and the asset named in *assetId*. |
| assetId               | **integer.** The ID of the asset (product) of the Exchange that caused the generation of the ticket. Usually, this is because of some problem or issue. |
| ticketId              | **string.** A unit ID (alphanumeric) assigned by the system to the ticket. |
| lastUpdatedTime       | **long integer.** The date and time stamp of the last update to the ticket, in POSIX format. All dates and times are UTC. |
| lastUpdatedBy         | **integer.** The user ID of the last user to update the ticket (this usually will be an admin). |
| ticketNumber          | **integer.** The number assigned to this ticket by the system. |
| assetManagerServiceId | **string.** The *assetManagerServiceId* is an alphanumeric string pre-configured for the specific Exchange. For current installations, this value always returns "1". |
| info                  | **string.** Any information appended to the ticket by the system. |
| ticketType        | **integer.** Describes the type of error or condition that triggered the ticket. One of:<br />**0** Unknown (an error condition)<br />**1** LowBalance<br />**2** HighBalance<br />**3** Transfer<br />**4** BalanceRequired<br />**5** BalanceMismatch<br />**6** WithdrawError<br />**7** DepositError<br />**8** AccountProviderError |
| ticketStatus      | **integer.** Describes the disposition of the ticket. One of:<br />**0** Unknown (an error condition)<br />**1** Open<br />**2** Resolved<br />**3** Rejected<br />**4** Notification |
