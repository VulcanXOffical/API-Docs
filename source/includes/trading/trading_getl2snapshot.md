## GetL2Snapshot

**Category:** Trading<br />
**Permissions:** Public<br />
**Call Type:** Synchronous

Provides a current Level 2 snapshot of a specific instrument trading on an Order Management System to a user-determined market depth. The Level 2 snapshot allows the user to specify the level of market depth information on either side of the bid and ask.

<aside class="notice">Depth in this call is "depth of market," the number of buyers and sellers at greater or lesser prices in the order book for the instrument.</aside>

### Request

```javascript
const { APEX } = require("VulcanX-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise('GetL2Snapshot',{
    OMSId: 1
    InstrumentId: 1,
    Depth: 100
})
```

```http
POST /AP/GetL2Snapshot HTTP/1.1
Host: hostname goes here...
Content-Type: application/json
Content-Length: 63

{
    "OMSId": 1,
    "InstrumentId": 1,
    "Depth": 100
}
```

| Key          | Value                                                                                                                                                                  |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| OMSId        | **integer**. The ID of the Order Management System where the instrument is traded._required._                                                                          |
| InstrumentId | **integer**. The ID of the instrument that is the subject of the snapshot._required._                                                                                  |
| Depth        | **integer**. Maximum number of bids and asks that can be included in the results. If set to 10, there can be maximum of 10 bids and 10 asks in the results._required._ |

### Response

```javascript
[
  [
    26, // MDUpdateId
    1, // Number of Unique Accounts
    1679559223042, //ActionDateTime in Posix format X 1000
    0, // ActionType 0 (New), 1 (Update), 2(Delete)
    29000, // LastTradePrice
    1, // Number of Orders
    28700, //Price
    1, // ProductPairCode
    0.5, // Quantity
    0, // Side 0 means buy and it is on the bid side
  ],
  [
    26,
    2,
    1679559223042,
    0,
    29000,
    2,
    29000,
    1,
    0.52,
    1, // Side 1 means sell and it is on the ask side
  ],
][
  // This is how the response is sent:

  [0, 1, 123, 0, 0.0, 0, 0.0, 0, 0.0, 0]
];
```

```http
[
    [
        26, // MDUpdateId
        1, // Number of Unique Accounts
        1679559223042, //ActionDateTime in Posix format X 1000
        0, // ActionType 0 (New), 1 (Update), 2(Delete)
        29000, // LastTradePrice
        1, // Number of Orders
        28700, //Price
        1, // ProductPairCode
        0.5, // Quantity
        0 // Side 0 means buy and it is on the bid side
    ],
    [
        26,
        2,
        1679559223042,
        0,
        29000,
        2,
        29000,
        1,
        0.52,
        1 // Side 1 means sell and it is on the ask side
    ]
]

// This is how the response is sent:

[[0,1,123,0,0.0,0,0.0,0,0.0,0]]
```

The response is an array of elements for one specific instrument, the number of elements corresponding to the market depth specified in the Request. It is sent as an uncommented, comma-delimited list of numbers. The example is commented. The _Level2UpdateEvent_ contains the same data, but is sent by the OMS whenever trades occur. To receive _Level2UpdateEvents_, a user must subscribe to _Level2UpdateEvents_.

| Key                       | Value                                                                                                                                                                                       |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| MDUpdateID                | **integer**. Market Data Update ID. This sequential ID identifies the order in which the update was created.                                                                                |
| Number of Unique Accounts | **integer**. Number of accounts that placed orders.                                                                                                                                         |
| ActionDateTime            | **long integer.**. _ActionDateTime_ identifies the time and date that the snapshot was taken or the event occurred, in POSIX format X 1000 (milliseconds since 1 January 1970).             |
| ActionType                | **integer**. L2 information provides price data. This value shows whether this data is:<br />**0** new<br />**1** update<br />**2** deletion                                                |
| LastTradePrice            | **real**. The price at which the instrument was last traded.                                                                                                                                |
| Number of Orders          | **integer**. Number of orders in the GetL2Snapshot.                                                                                                                                         |
| Price                     | **real**. Bid or Ask price for the Quantity (see _Quantity_ below).                                                                                                                         |
| ProductPairCode           | **integer**. _ProductPairCode_ is the same value and used for the same purpose as _InstrumentID_. The two are completely equivalent. _InstrumentId_ 47 = _ProductPairCode_ 47.              |
| Quantity                  | **real**. Quantity available at a given Bid or Ask price (see _Price_ above).                                                                                                               |
| Side                      | **integer**. One of:<br />**0** Buy means it is on the bid side<br />**1** Sell means it is on the ask side<br />**2** Short (reserved for future use)<br />**3** Unknown (error condition) |
