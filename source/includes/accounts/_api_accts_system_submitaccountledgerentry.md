## SubmitAccountLedgerEntry

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Submits a ledger entry.

### Request

```json
{
    "omsId": 0,
    "accountId": 0,
    "productId": 0,
    "cR_Amt": 0.0,
    "dR_Amt": 0.0,
    "comment": "",
    "oneSidedTransaction": false,
    "doNotAffectBalance": false,
    "balance": 0.0,
    "transactionTime": "0001-01-01T00:00:00",
    "counterPartyId": 0,
    "transactionType": 0,
    "transactionReferenceType": 0,
    "accountChangeReason": 0,
    "PreventNegatives": true
}
```
Some key-value pairs are required. The rest are optional.

| Key                      | Value                                                        |
| ------------------------ | ------------------------------------------------------------ |
| omsId                    | **integer.**  REQUIRED The ID of the Order Management System where the ledger resides. |
| accountId                | **integer.** REQUIRED The ID of the account for which the ledger entry is made. |
| productId                | **integer.** REQUIRED The ID of the product being deposited or withdrawn. |
| cR_Amt                   | **real.** REQUIRED Credit entry. The amount of product entering the account. |
| dR_Amt                   | **real.** REQUIRED Debit entry. The amount of product leaving the account. |
| comment                  | **string.** REQUIRED Any comment appended to the ledger entry. |
| oneSidedTransaction      | **Boolean.** The value is *true* for a manual entry where the user must make either a deposit or a withdrawal entry only. |
| doNotAffectBalance       | **Boolean.** If *true,* then this ledger entry does not affect the balance of the account &mdash; it is only a transaction being recorded in the account. When *true,* you must enter a value for the *balance* key-value pair. If *false,* then the ledger entry does affect the balance.  |
| balance                  | **real.** Only used when the *balance* key-value pair is *true.* Because a non-balance-affecting ledger entry is for recording purposes only, this key-value pair provides the balance information to prevent a true calculation. If *balance* is *false,* set this value to 0.0.    |
| transactionTime          | **string.** The time that the ledge entry was made, in Microsoft Ticks format and UTC time zone. |
| counterPartyId           | **integer.** The ID of the other party (the non-*accountId* party) in a ledger entry. |
| transactionType          | **integer.** A number representing the type of transaction for this ledger entry. One of<br />**1** Fee<br />**2** Trade<br />**3** Other<br />**4** Reverse<br />**5** Hold<br />**6** Rebate<br />**7** MarginAcquisition<br />**8** MarginRelinquish |
| transactionReferenceType | **integer.** A number representing the type of action or event that caused the ledger entry. One of:<br />**1** Trade<br />**2** Deposit<br />**3** Withdraw<br />**4** Transfer<br />**5** OrderHold<br />**6** WithdrawHold<br />**7** DepositHold<br />**8** MarginHold<br />**9** ManualHold<br />**10** ManualEntry<br />**11** MarginAcquisition<br />**12** MarginRelinquish<br />**13** MarginQuoteHold |
| accountChangeReason      | **integer.** The reason you are making this ledger adjustment. One of:<br />**0** Unknown<br />**1** OrderPlaced<br />**2** OrderCancelled<br />**3** OrderExecution<br />**4** Deposit<br />**5** Withdraw<br />**6** Admin<br />**7** Fee<br />**8** OrderModified<br />**9** Manual<br />**10** Rebate<br />**11** Transfer<br />**12** MarginQuotePlaced |
| PreventNegatives         | **Boolean.** Instructs the OMS to reject this request if the resulting balance of the account will be negative. |

### Response

```json
{
    "accountId": 0,
    "productId": 0,
    "cR_Amt": 0.0,
    "dR_Amt": 0.0,
    "enteredBy": 0,
    "comments": "",
    "oneSidedTransaction": 0,
    "accountLedgerEntryId": 0,
    "timestamp": 158153615438
}
```
The Response is a confirmation of the ledger entry values.

| Key                  | Value                                                        |
| -------------------- | ------------------------------------------------------------ |
| accountId            | **integer.** The ID of the account for which the ledger entry was made. |
| productId            | **integer.** The ID of the product being deposited or withdrawn. |
| cR_Amt               | **real.** Credit entry. The amount of funds entering the account. |
| dR_Amt               | **real.** Debit entry. The amount of funds leaving the account. |
| enteredBy            | **integer.** The ID of the user who made the ledger entry.   |
| comments             | **string.** Any comment previously entered about the ledger entry. |
| oneSidedTransaction  | **byte.** Used for a manual entry when the user must make either a deposit or a withdrawal entry. |
| AccountLedgerEntryId | **long integer.** The ID of this ledger entry.               |
| timestamp            | **long integer.** epoch milliseconds. |