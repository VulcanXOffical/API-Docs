## GetOpenWithdrawHolds

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Returns an array of all withdrawal transactions for the specified *accountId* and *TransactionReferenceType* that currently have open withdrawal holds.

### Request

```json
{
    "omsId": 0,
    "accountId": 0,
    "TransactionReferenceType": ""
}
```

| Key                      | Value                                                        |
| ------------------------ | ------------------------------------------------------------ |
| omsId                    | **integer.** The ID of the Order Management System where the transaction took place. |
| accountId                | **integer.** The ID of the account whose open holds you want to return. |
| TransactionReferenceType | **integer.**                                                 |

### Response 

```json
[
    {
        "transactionId": 0,
        "omsId": 0,
        "accountId": 0,
        "cr": 0.0,
        "dr": 0.0,
        "counterparty": 0,
        "TransactionType": "",
        "ReferenceType": "",
        "referenceId": 0,
        "productId": 0,
        "balance": 0.0,
        "timeStamp": 0
    }
]
```

| Key             | Value                                                        |
| --------------- | ------------------------------------------------------------ |
| transactionId   | **integer.** The ID of the transaction.                      |
| omsId           | **integer.** The ID of the Order Management System where the held transaction took place. |
| accountId       | **integer.** The ID of the account whose transaction triggered a hold. |
| cr              | **real.** Credit entry for the account on the order book. Funds entering an account. |
| dr              | **real.** Debit entry for the account on the order book. Funds leaving an account. |
| counterparty    | **long integer.** The corresponding party in a trade.        |
| TransactionType | **string.** A phrase representing the type of transaction that caused the hold. One of:<br />**1** Fee<br />**2** Trade<br />**3** Other<br />**4** Reverse<br />**5** Hold<br />**6** Rebate<br />**7** MarginAcquisition<br />**8** MarginRelinquish |
| ReferenceType   | **string.** A phrase representing the type of action or even that triggered the transaction that caused the hold. One of:<br />**1** Trade<br />**2** Deposit<br />**3** Withdraw<br />**4** Transfer<br />**5** OrderHold<br />**6** WithdrawHold<br />**7** DepositHold<br />**8** MarginHold<br />**9** ManualHold<br />**10** ManualEntry<br />**11** MarginAcquisition<br />**12** MarginRelinquish<br />**13** MarginQuoteHold |
| referenceId     | **long integer.** The ID of the action or event that triggered the transaction causing the hold. |
| productId       | **integer.** The ID of the product on this account's side of the transaction. For example, in a dollars-for-BitCoin transaction, one side will have the product Dollar and the other side will have the product BitCoin. Use **GetProduct** to return information about a product based on its ID. |
| balance         | **real.** The balance in the account after the transaction.  |
| timeStamp       | **long integer.** Time at which the transaction took place, in POSIX format and UTC time zone. Epoch milliseconds. |


