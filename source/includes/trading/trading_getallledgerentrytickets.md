## GetAllLedgerEntryTickets

**Category:** Trading<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

Retrieves account ledger entries for a specific account.

Results can also be filtered according to optional search parameters such as **ProductId**, other optional parameters are defined in the request key-value table below.

It is also possible to filter according to **AccountLedgerEntryId**.

A user with Trading permission can only retrieve ledger entries for accounts it is associated with; a user with Operator permission can retrieve ledger entries for any account.

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("GetAllLedgerEntryTickets", {
  OMSId: 1,
  AccountId: 7,
});
```

```http
POST /AP/GetAllLedgerEntryTickets HTTP/1.1
Host: hostname goes here...
aptoken: c5f917b9-f173-4c29-a615-1503d2e78023 //valid sessiontoken
Content-Type: application/json
Content-Length: 41

{
    "OMSId": 1,
    "AccountId": 9
}
```

| Key                  | Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| OMSId                | **integer**. The ID of the Order Management System on which the orders took place._required._                                                                                                                                                                                                                                                                                                                                                                                             |
| AccountId            | **integer**. The account ID for which the ledger entry was executed for._required._                                                                                                                                                                                                                                                                                                                                                                                                       |
| ProductId            | **integer.** The product which was either debited or credited to the account. Can be used to filter results._optional._                                                                                                                                                                                                                                                                                                                                                                   |
| EnteredBy            | **integer.** The id of the user who submitted the account ledger entry. Can be used to filter results._optional._                                                                                                                                                                                                                                                                                                                                                                         |
| AccountLedgerEntryId | **integer**. The Id of the actual ledger entry. If value is 0(the same as not putting the filter), results will have all the ledger entries for the specific account, if value is greater than 0 and exactly matches a ledger entry for the specific account, it will result to just one ledger entry being returned as 1 id represents exactly 1 ledger entry, if the id does not match any account ledger entry for the specific account, the result will be an empty array._optional._ |

### Response

```javascript
[
  {
    AccountId: 9,
    ProductId: 16,
    CR_Amt: 1000000.0,
    DR_Amt: 0.0,
    EnteredBy: 1,
    Comments: [""],
    OneSidedTransaction: 0,
    AccountLedgerEntryId: 3519,
    TimeStamp: 1676542115034,
    Status: "Accepted",
    RejectReason: 0,
    AccountChangeReason: "Manual",
    CounterPartyId: 3,
    DoNotAffectBalance: false,
    TransactionType: "Other",
    TransactionReferenceType: "ManualEntry",
  },
  {
    AccountId: 9,
    ProductId: 2,
    CR_Amt: 1.0,
    DR_Amt: 0.0,
    EnteredBy: 1,
    Comments: [""],
    OneSidedTransaction: 0,
    AccountLedgerEntryId: 3509,
    TimeStamp: 1676260561012,
    Status: "Accepted",
    RejectReason: 0,
    AccountChangeReason: "Manual",
    CounterPartyId: 3,
    DoNotAffectBalance: false,
    TransactionType: "Other",
    TransactionReferenceType: "ManualEntry",
  },
];
```

```http
[
    {
        "AccountId": 9,
        "ProductId": 16,
        "CR_Amt": 1000000.0000000000000000000000,
        "DR_Amt": 0.0000000000000000000000000000,
        "EnteredBy": 1,
        "Comments": [
            ""
        ],
        "OneSidedTransaction": 0,
        "AccountLedgerEntryId": 3519,
        "TimeStamp": 1676542115034,
        "Status": "Accepted",
        "RejectReason": 0,
        "AccountChangeReason": "Manual",
        "CounterPartyId": 3,
        "DoNotAffectBalance": false,
        "TransactionType": "Other",
        "TransactionReferenceType": "ManualEntry"
    },
    {
        "AccountId": 9,
        "ProductId": 2,
        "CR_Amt": 1.0000000000000000000000000000,
        "DR_Amt": 0.0000000000000000000000000000,
        "EnteredBy": 1,
        "Comments": [
            ""
        ],
        "OneSidedTransaction": 0,
        "AccountLedgerEntryId": 3509,
        "TimeStamp": 1676260561012,
        "Status": "Accepted",
        "RejectReason": 0,
        "AccountChangeReason": "Manual",
        "CounterPartyId": 3,
        "DoNotAffectBalance": false,
        "TransactionType": "Other",
        "TransactionReferenceType": "ManualEntry"
    }
]
```

Returns an array of objects, each object represents a ledger entry. The call returns an empty array if there are no ledger entries for the account.

| Key                      | Value                                                                                                                                                                                                                                                                                                                                                                         |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AccountId                | **integer**. The account ID for which the ledger entry was executed for. Or the account which was either debited or credited.                                                                                                                                                                                                                                                 |
| ProductId                | **integer.** The product which was either debited or credited to the account.                                                                                                                                                                                                                                                                                                 |
| CR_Amt                   | **real** The amount credited, if value is greater than 0, it means the account was credited.                                                                                                                                                                                                                                                                                  |
| DR_Amt                   | **real** The amount debited, if value is greater than 0, it means the account was debited.                                                                                                                                                                                                                                                                                    |
| EnteredBy                | **integer.** The id of the user who submitted the account ledger entry.                                                                                                                                                                                                                                                                                                       |
| Comments                 | **string**. Any note or comment entered for the ledger entry.                                                                                                                                                                                                                                                                                                                 |
| AccountLedgerEntryId     | **integer**. The Id of the actual ledger entry.                                                                                                                                                                                                                                                                                                                               |
| TimeStamp                | **long integer**. Time stamp of the order in POSIX format x 1000 (milliseconds since 1/1/1970 in UTC time zone)                                                                                                                                                                                                                                                               |
| Status                   | **string**. The status of the ledger entry                                                                                                                                                                                                                                                                                                                                    |
| RejectReason             | **string**. The reason why the ledger entry was rejected.                                                                                                                                                                                                                                                                                                                     |
| AccountChangeReason      | **string**. Always **Manual** since a ledger entry is a ManualEntry TransactionReferenceType.                                                                                                                                                                                                                                                                                 |
| CounterPartyId           | **integer**. The id of the counterparty account. If the accountid was debited, the counterpartyid was credited. Usually has a value of 3, it is the OMS Liability Account. If CounterpartyId was set to a value other than 3, the counterpart transaction either debit or credit will happen to the specific id and it will be the one to reflect as the value of this field. |
| TransactionType          | **string**. Always **Other** since a ledger entry is classified as TransactionType **Other**.                                                                                                                                                                                                                                                                                 |
| TransactionReferenceType | **string**. Always **ManualEntry** since a ledger entry is classified as a TransactionReferenceType **ManualEntry**.                                                                                                                                                                                                                                                          |
