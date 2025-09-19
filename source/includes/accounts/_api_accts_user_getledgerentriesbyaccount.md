## GetLedgerEntriesByAccount

**Category:** User<br />
**Permissions:** Operator<br />
**Call Type:** Synchronous

Retrieves an array of an account's ledger entries by account ID.

### Request

```json
{
    "AccountId": 1
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| AccountId | **integer.** The ID of the account whose ledger entries you want to retrieve. |

### Response

```json
[
    {
        "accountId":0,
        "productId":0,
        "cR_Amt":0.0,
        "dR_Amt":0.0,
        "enteredBy":0,
        "comments":null,
        "oneSidedTransaction":0,
        "accountLedgerEntryId":0
    }
]
```
The response consists of an array, each element describing a ledger entry.

| Key                  | Value                                                        |
| -------------------- | ------------------------------------------------------------ |
| accountId            | **integer.** The ID of the account into which the ledger entry was made. |
| productId            | **integer.** The ID of the product being credited or debited to the account. |
| cR_Amt               | **real.** Credit amount. Funds entering the account.         |
| dR_Amt               | **real.** Debit amount. Funds leaving the account.           |
| enteredBy            | **integer.** The ID of the person who made the ledger entry. |
| comments             | **string.** Any comment made on the ledger entry.            |
| oneSidedTransaction  | **byte.** Used for a manual entry when the user must make either a deposit or a withdrawal entry. |
| accountLedgerEntryId | **long integer.** The ID of the ledger entry for the account. |


