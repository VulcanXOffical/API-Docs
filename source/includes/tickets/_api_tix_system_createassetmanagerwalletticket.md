## CreateAssetManagerWalletTicket

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Creates an Asset Manager wallet ticket, and returns the ticket number and the ticket status.

The Asset Manager wallet is a joint wallet for all Account Providers on the Exchange. Asset Manager wallet tickets are system-generated tickets that alert an admin (Operator) to error conditions that may occur between the Exchange and its Account Providers.

Only a user with Operator permission may create an Asset Manager wallet ticket.

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
| accountProviderId       | **integer.** The ID of the Account Provider that is linked to the Asset Manager. |
| assetId                | **integer.** The ID of the asset (product) of the Exchange that caused the generation of a ticket. Usually this is because of some problem or issue. |
| ticketId               | **string.** A GUID (alphanumeric) assigned by the system to the ticket. When creating a ticket, leave this as an empty string. |
| ticketType        | **integer.** Describes the type of error or condition that triggered the ticket. One of:<br />**0** Unknown (an error condition)<br />**1** LowBalance<br />**2** HighBalance<br />**3** Transfer<br />**4** BalanceRequired<br />**5** BalanceMismatch<br />**6** WithdrawError<br />**7** DepositError<br />**8** AccountProviderError |
| ticketStatus      | **integer.** Describes the disposition of the ticket. One of:<br />**0** Unknown (an error condition)<br />**1** Open<br />**2** Resolved<br />**3** Rejected<br />**4** Notification |
| ticketNumber           | **integer.** The number of this ticket on the Exchange. When creating a ticket, leave this value empty. The system will create a ticket number and send it in the Response. |
| assetManagerService Id | **string.** The *assetManagerServiceId* is an alphanumeric string pre-configured for the specific Exchange. For current installations, this value is "1". |
| startIndex             | **integer.** The **CreateAssetManagerWalletTicket** call ignores the value for *startIndex*. You can safely set this value to 0. |
| limit                  | **integer.** The **CreateAssetManagerWalletTicket** call ignores the value for *limit.* You can safely set this value to 0. |

### Response

```json
{
    "success": true,
    "ticketnumber": 100000002
}
```

The successful response to **CreateAssetManagerWalletTicket** is a Boolean *true* value and a ticket number to identify the ticket.

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| success      | **Boolean.** Returns *true* if the Asset Manager wallet ticket is successfully created; *false* if the ticket is not successfully created. |
| ticketnumber | **long integer.** The number of the ticket, created by the Exchange. |
