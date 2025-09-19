## GetAccountTransactions

**Category:** Trading<br />
**Permissions:** Trading, AccountReadOnly<br />
**Call Type:** Synchronous

Gets a list of transactions for an account.

Results can be filtered using different search parameters such as **TransactionType** and **ProductId**, other optional fields that can serve as search parameter are defined in the request key value table below.

<aside class="notice"><strong>Note:</strong> In this call, “Depth” refers not to the depth of the order book, but to the count of trades to report.</aside>

### Request

```javascript
const { APEX } = require("VulcanX-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("GetAccountTransactions", {
  OMSId: 1,
  AccountId: 7,
  TransactionReferenceTypes: ["Deposit", "Withdraw"],
  ProductId: 3,
});
```

```http
POST /AP/GetAccountTransactions HTTP/1.1
Host: apialphapointuniversitystaging.cdnhop.net:8443
aptoken: 15a9b337-94c4-4e11-a051-287725519a45
Content-Type: application/json
Content-Length: 91

{
    "OMSId": 1,
    "AccountId": 7,
    "TransactionReferenceTypes": ["Deposit", "Withdraw"],
    "ProductId": 3
}
```

| Key                       | Value                                                                                                                                                                                                                                                                                                       |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| OMSId                     | **integer.** The ID of the Order Management System from which the account’s transactions will be returned.                                                                                                                                                                                                  |
| AccountId                 | **integer.** The ID of the account for which transactions will be returned. If the authenticated user has elevated permission like Operator or AccountOperator, account id is not required, results to be returned will be the transactions of the authenticated user's account/s._conditionally required._ |
| Depth                     | **integer.** The number of transactions that will be returned, starting with the most recent transaction. If not defined, all transactions of the account will be returned(assuming not other search parameters are defined)._optional._                                                                    |
| ProductId                 | **integer.** Can be used to filter results, if set, only transactions for the specific product id specified will be returned, else, all transactions regardless of the product will be returned(assuming not other search parameters are defined)._optional._                                               |
| TransactionId             | **integer.** Can be used to filter results, if set, only transaction with the specific id specified will be returned, else, all transactions regardless of the transaction id will be returned(assuming not other search parameters are defined)._optional._                                                |
| ReferenceId               | **integer.** Can be used to filter results, if set, only transaction with the specific id specified will be returned, else, all transactions regardless of the reference id will be returned(assuming not other search parameters are defined)._optional._                                                  |
| TransactionTypes          | **array of string or integer type.** Can be used to filter results according to transaction type/s(can filter with either just 1 or more). If not set, transactions with any transaction type will be returned._optional._                                                                                  |
| TransactionReferenceTypes | **array of string or integer type.** Can be used to filter results according to transaction reference type/s(can filter with either just 1 or more). If not set, transactions with any transaction reference type will be returned._optional._                                                              |
| StartTimestamp            | **long integer.** Can be used to filter results based on timestamp the transaction has happened. This filter will return transactions that happened on or after(earliest possible time) the specified timestamp value, if not set, transactions that happened any time will be returned._optional._         |
| EndTimeStamp              | **long integer.** Can be used to filter results based on timestamp the transaction has happened. This filter will return transactions that happened on or before(latest possible time) the specified timestamp value, if not set, transactions that happened any time will be returned._optional._          |

### TransactionTypes Enums

**1** Fee<br />
**2** Trade<br />
**3** Other<br />
**4** Reverse<br />
**5** Hold<br />
**6** Rebate<br />
**7** MarginAcquisition<br />
**8** MarginRelinquishByTrade<br />
**9** MarginInterestTransfer<br />
**10** MarginOperatorTransferToMarginAccount<br />
**11** MarginOperatorTransferToAssetAccount<br />
**12** MarginUserTransfer<br />
**13** MarginRelinquishByTransfer<br />
**14** MarginRelinquishByReverseTrade<br />
**15** Distribution<br />
**16** Payment<br />
**21** OperatorLend<br />
**22** OperatorReceived<br />
**23** Rebalance<br />
**24** Commission<br />
**25** AirDrop<br />

### TransactionReferenceTypes Enums

**1** Trade<br />
**2** Deposit<br />
**3** Withdraw<br />
**4** Transfer<br />
**5** OrderHold<br />
**6** WithdrawHold<br />
**7** DepositHold<br />
**8** MarginHold<br />
**9** ManualHold<br />
**10** ManualEntry<br />
**11** MarginAcquisition<br />
**12** MarginRelinquish<br />
**13** MarginInterestNetting<br />
**14** MarginOperatorTransferToMarginAccount<br />
**15** MarginOperatorTransferToAssetAccount<br />
**16** MarginUserTransfer<br />
**17** MarginPositionReverseTrade<br />
**18** AffiliateRebate<br />
**19** DistributionEntry<br />
**20** TransferHold<br />
**21** AirDrop<br />

### Response

```javascript
[
  {
    TransactionId: 24214,
    ReferenceId: 294,
    OMSId: 1,
    AccountId: 7,
    CR: 0.01247667,
    DR: 0.0,
    Counterparty: 3,
    TransactionType: "Other",
    ReferenceType: "Deposit",
    ProductId: 3,
    Balance: 1.138154399436,
    TimeStamp: 1678904016338,
  },
  {
    TransactionId: 24021,
    ReferenceId: 293,
    OMSId: 1,
    AccountId: 7,
    CR: 0.01247667,
    DR: 0.0,
    Counterparty: 3,
    TransactionType: "Other",
    ReferenceType: "Deposit",
    ProductId: 3,
    Balance: 1.125677729436,
    TimeStamp: 1678706804112,
  },
  {
    TransactionId: 23403,
    ReferenceId: 292,
    OMSId: 1,
    AccountId: 7,
    CR: 0.01311447,
    DR: 0.0,
    Counterparty: 3,
    TransactionType: "Other",
    ReferenceType: "Deposit",
    ProductId: 3,
    Balance: 1.122515996076,
    TimeStamp: 1677575188002,
  },
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
];
```

```http
[
    {
        "TransactionId": 24214,
        "ReferenceId": 294,
        "OMSId": 1,
        "AccountId": 7,
        "CR": 0.0124766700000000000000000000,
        "DR": 0.0000000000000000000000000000,
        "Counterparty": 3,
        "TransactionType": "Other",
        "ReferenceType": "Deposit",
        "ProductId": 3,
        "Balance": 1.1381543994360000000000000000,
        "TimeStamp": 1678904016338
    },
    {
        "TransactionId": 24021,
        "ReferenceId": 293,
        "OMSId": 1,
        "AccountId": 7,
        "CR": 0.0124766700000000000000000000,
        "DR": 0.0000000000000000000000000000,
        "Counterparty": 3,
        "TransactionType": "Other",
        "ReferenceType": "Deposit",
        "ProductId": 3,
        "Balance": 1.1256777294360000000000000000,
        "TimeStamp": 1678706804112
    },
    {
        "TransactionId": 23403,
        "ReferenceId": 292,
        "OMSId": 1,
        "AccountId": 7,
        "CR": 0.0131144700000000000000000000,
        "DR": 0.0000000000000000000000000000,
        "Counterparty": 3,
        "TransactionType": "Other",
        "ReferenceType": "Deposit",
        "ProductId": 3,
        "Balance": 1.1225159960760000000000000000,
        "TimeStamp": 1677575188002
    },
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
    }
]
```

The response returns an array of objects, each object represents a transaction.

| Key             | Value                                                                                                                                                                                                                                                                                                                                                          |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| transactionId   | **Integer.** The ID of the transaction.                                                                                                                                                                                                                                                                                                                        |
| omsId           | **Integer.** The ID of the Order Management System under which the requested transactions took place.                                                                                                                                                                                                                                                          |
| accountId       | **Integer.** The single account under which the transactions took place.                                                                                                                                                                                                                                                                                       |
| cr              | **real.** Credit entry for the account on the order book. Funds entering an account.                                                                                                                                                                                                                                                                           |
| dr              | **real.** Debit entry for the account on the order book. Funds leaving an account.                                                                                                                                                                                                                                                                             |
| counterparty    | **long integer.** The corresponding party in a trade.                                                                                                                                                                                                                                                                                                          |
| transactionType | **integer.** A number representing the type of transaction:<br />1 Fee<br />2 Trade<br />3 Other<br />4 Reverse<br />5 Hold<br />6 Rebate<br />7 MarginAcquisition<br />8 MarginRelinquish                                                                                                                                                                     |
| referenceId     | **long integer.** The ID of the action or event that triggered this transaction.                                                                                                                                                                                                                                                                               |
| referenceType   | **integer.** A number representing the type of action or event that triggered this transaction. One of:<br />1 Trade<br />2 Deposit<br />3 Withdraw<br />4 Transfer<br />5 OrderHold<br />6 WithdrawHold<br />7 DepositHold<br />8 MarginHold<br />9 ManualHold<br />10 ManualEntry<br />11 MarginAcquisition<br />12 MarginRelinquish<br />13 MarginQuoteHold |
| productId       | **integer.** The ID of the product on this account’s side of the transaction. For example, in a dollars-for-BitCoin transaction, one side will have the product Dollar and the other side will have the product BitCoin. Use **GetProduct** to return information about a product based on its ID.                                                             |
| balance         | **real.** The balance in the account after the transaction.                                                                                                                                                                                                                                                                                                    |
| timeStamp       | **long integer.** Time at which the transaction took place, in POSIX format.                                                                                                                                                                                                                                                                                   |
