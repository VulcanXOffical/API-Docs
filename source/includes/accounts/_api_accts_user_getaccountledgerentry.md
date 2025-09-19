## GetAccountLedgerEntry

**Category:** User<br />
**Permissions:** Operator<br />
**Call Type:** Synchronous

Retrieves a single ledger entry for an account by the ID of the ledger entry. You can obtain a list of ledger entry IDs for a specific account with the call **GetLedgerEntriesByAccount.** 

### Request

```json
{
    "AccountLedgerEntryId": 1
}
```

| Key                  | Value                                                      |
| -------------------- | ---------------------------------------------------------- |
| AccountLedgerEntryId | **integer.** The ID of the ledger entry you want returned. |

### Response

```json
{
    "AccountId": 0,
    "ProductId": 0,
    "CR_Amt": 0,
    "DR_Amt": 0,
    "EnteredBy": 0,
    "Comments": null,
    "OneSidedTransaction": 0,
    "AccountLedgerEntryId": 0,
    "timestamp": 158153615438
}
```

The response is list of fields describing the ledger entry.

| Key                       | Value                                                        |
| ------------------------- | ------------------------------------------------------------ |
| AccountId                 | **integer.** The ID of the account for which the ledger entry was made. |
| ProductId                 | **integer.** The ID of the product being deposited or withdrawn. |
| CR_Amt                    | **real.** Credit entry. The amount of funds entering the account. |
| DR_Amt                    | **real.** Debit entry. The amount of funds leaving the account. |
| EnteredBy                 | **integer.** The ID of the user who made the ledger entry.   |
| Comments                  | **string.** Any comment previously entered about the ledger entry. |
| oneSidedTransaction       | **byte.** Used for a manual entry when the user must make either a deposit or a withdrawal entry. |
| AccountLedgerEntryId      | **long integer.** The ID of this ledger entry.                     |
| timestamp                 | **long integer.** epoch milliseconds. |
