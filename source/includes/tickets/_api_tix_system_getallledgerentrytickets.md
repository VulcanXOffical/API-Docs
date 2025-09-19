## GetAllLedgerEntryTickets

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Retrieves an account ledger entries by optional parameters

Only a user with Operator permission can issue **GetAllLedgerEntryTickets.**

### Request

```json
{
    "OMSId": 1,
    "OperatorId": 1,
    "StartIndex": 0,
    "Limit": 0
}
```

The values for *OMSId* is required; the key-value pairs *StartIndex* and *Limit* are optional. You can include *StartIndex*, *Limit,* or both.

| Key            | Value                                                        |
| -------------- | ------------------------------------------------------------ |
| OMSId          | **integer.** REQUIRED The ID of the Order Management System on which the ledger entries were created. |
| AccountId      | **integer.** OPTIONAL The ID of the Account for which the ledger entries were created. |
| UserId         | **integer.** OPTIONAL The ID of the User for which the ledger entries were created. |
| ProductId      | **integer.** OPTIONAL The ID of the Product for which the ledger entries were created. |
| StartIndex     | **integer.** OPTIONAL The earliest location in the series of ledger entries at which to begin returning tickets. Tickets are returned from that location forward (that is, from then toward now). The most recent deposit ticket is ticket 0. If you do not include a *StartIndex* key and value in your request, tickets from the beginning of the Exchange will be returned (subject to *Limit.*) |
| Limit          | **integer.** OPTIONAL The count of deposit tickets you want returned. For example, if you set the value of *Limit* to 50, a maximum of 50 ledger entries will be returned. That maximum may be further restricted by the position of *StartIndex.* For example, if your *StartIndex* is only ten tickets back, and you include a *Limit* value of 50, you're still only going to get ten tickets. |

### Response

```json
[
    {
        "accountLedgerEntryId": 0,
        "accountId": 0,
        "productId": 0,
        "CR_Amt": 0.0,
        "DR_Amt": 0.0,
        "enteredBy": 0.0,
        "comments": "",
        "onsSidedTransaction": false,
        "timestamp": 158153615438
    },
]
```

The Response returns an array of ledger entries matching the criteria set in the Request.

| Key             | Value                                                        |
| --------------- | ------------------------------------------------------------ |
| accountLedgerEntryId  | **integer.** The ID of the Ledger Entry |
| accountId       | **integer.** The ID of the product into which the deposit was made. |
| assetId         | **integer.** The ID of the asset (product) deposited. This may be cryptocurrency or fiat (national) currency. |
| productId       | **string.** The short name of the asset being deposited, for example USD (US Dollars), BTC (BitCoin), etc. |
| CR_Amt          | **real.** The Credit amount of the ledger entry. |
| DR_Amt           | **real.** The Debit amount of the ledger entry. |
| comments     | **string.** The Comments entered at time of creation. |
| onsSidedTransaction       | **boolean.** One-sided (false by default). |
| timestamp | **long integer.** epoch milliseconds. |

