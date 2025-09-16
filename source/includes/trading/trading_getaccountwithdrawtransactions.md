## GetAccountWithdrawTransactions

**Category:** Trading<br />
**Permissions:** Trading, AccountReadOnly<br />
**Call Type:** Synchronous

Gets a list of withdraws for an account.

Users with Trading and AccountReadOnly permission can get withdraw transactions only for the account/s with which they are associated. Users with Operator permission can get withdraw transactions for any account.

The owner of the trading venue determines how long to retain transaction history before archiving.

<aside class="notice"><strong>Note: </strong>Depth in this call is a count of how many withdraw transactions to report. It is not "depth of market."</aside>

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("GetAccountWithdrawTransactions", {
  OMSId: 1,
  AccountId: 7,
});
```

```http
POST /AP/GetAccountWithdrawTransactions HTTP/1.1
Host: hostname goes here...
aptoken: c5f917b9-f173-4c29-a615-1503d2e78023 //valid sessiontoken
Content-Type: application/json
Content-Length: 41

{
    "OMSId": 1,
    "AccountId": 7
}
```

| Key       | Value                                                                                                       |
| --------- | ----------------------------------------------------------------------------------------------------------- |
| OMSId     | **integer.** The ID of the Order Management System on which the account transactions took place._required._ |
| AccountId | **integer.** The ID of the account whose transactions will be returned._required._                          |
| Depth     | **integer.** The count of withdraw transactions to be returned._optional._                                  |

### Response

```javascript
[
  {
    TransactionId: 22693,
    ReferenceId: 286,
    OMSId: 1,
    AccountId: 7,
    CR: 0.0,
    DR: 0.00001,
    Counterparty: 3,
    TransactionType: "Other",
    ReferenceType: "Withdraw",
    ProductId: 3,
    Balance: 1.11033172,
    TimeStamp: 1676348233473,
  },
  {
    TransactionId: 22671,
    ReferenceId: 281,
    OMSId: 1,
    AccountId: 7,
    CR: 0.0,
    DR: 1.0,
    Counterparty: 2,
    TransactionType: "Fee",
    ReferenceType: "Withdraw",
    ProductId: 1,
    Balance: 1020604462.5137057184022,
    TimeStamp: 1676346027780,
  },
];
```

```http
[
    {
        "TransactionId": 22693,
        "ReferenceId": 286,
        "OMSId": 1,
        "AccountId": 7,
        "CR": 0.0000000000000000000000000000,
        "DR": 0.0000100000000000000000000000,
        "Counterparty": 3,
        "TransactionType": "Other",
        "ReferenceType": "Withdraw",
        "ProductId": 3,
        "Balance": 1.1103317200000000000000000000,
        "TimeStamp": 1676348233473
    },
    {
        "TransactionId": 22671,
        "ReferenceId": 281,
        "OMSId": 1,
        "AccountId": 7,
        "CR": 0.0000000000000000000000000000,
        "DR": 1.0000000000000000000000000000,
        "Counterparty": 2,
        "TransactionType": "Fee",
        "ReferenceType": "Withdraw",
        "ProductId": 1,
        "Balance": 1020604462.5137057184022000000,
        "TimeStamp": 1676346027780
    }
]
```

The response returns an array of objects, each object represents a withdraw transaction.

| Key              | Value                                                                                                                                        |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| TransactionId    | **Integer.** The ID of the transaction.                                                                                                      |
| OMSId            | **Integer.** The ID of the Order Management System under which the requested transactions took place.                                        |
| AccountId        | **Integer.** The single account under which the transactions took place.                                                                     |
| CR               | **real.** Credit entry for the account on the order book. Funds entering an account.                                                         |
| DR               | **real.** Debit entry for the account on the order book. Funds leaving an account.                                                           |
| Counterparty     | **long integer.** The corresponding party in a trade.                                                                                        |
| TransacitionType | **string.** A withdraw transaction is always **Other** TransactionType.                                                                      |
| ReferenceId      | **long integer.** The ID of the action or event that triggered this transaction.                                                             |
| ReferenceType    | **string.** A withdraw transaction is always a **withdraw** ReferenceType                                                                    |
| ProductId        | **integer.** The ID of the product in which the withdraw was made. Use **GetProduct** to return information about a product based on its ID. |
| Balance          | **real.** The balance in the account after the withdraw transaction.                                                                         |
| Timestamp        | **long integer.** Time at which the transaction took place, in POSIX format.                                                                 |
