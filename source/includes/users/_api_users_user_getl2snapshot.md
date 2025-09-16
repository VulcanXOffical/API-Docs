## GetL2Snapshot

**Category:** User<br />**Permissions:** Public<br />**Call Type:** Synchronous

Provides a current Level 2 snapshot of a specific instrument trading on an Order Management System to a user-determined market depth. The Level 2 snapshot allows the user to specify the level of market depth information on either side of the bid and ask.

<aside class="notice">Depth in this call is "depth of market," the number of buyers and sellers at greater or lesser prices in the order book for the instrument.</aside>

### Request

```json
{
  "OMSId": 1,
  "InstrumentId": 1,
  "Depth": 100 
}
```

| Key       | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| OMSId        | **integer**. The ID of the Order Management System where the instrument is traded. |
| InstrumentId | **integer**. The ID of the instrument that is the subject of the snapshot. |
| Depth        | **integer**. Depth of the market — the number of buyers and sellers at greater or lesser prices in the order book for the instrument. Defaults to 100. |

### Response
```json
[
    [
        0, // MDUpdateId        
        1, // Number of Unique Accounts
        123,// ActionDateTime in Posix format X 1000
        0,   // ActionType 0 (New), 1 (Update), 2(Delete)
        0.0, // LastTradePrice
        0, // Number of Orders
        0.0, //Price
        0,  // ProductPairCode
        0.0, // Quantity
        0, // Side
    ],
]

// This is how the response is sent:

[[0,1,123,0,0.0,0,0.0,0,0.0,0]]
```
The response is an array of elements for one specific instrument, the number of elements corresponding to the market depth specified in the Request. It is sent as an uncommented, comma-delimited list of numbers. The example is commented. The *Level2UpdateEvent* contains the same data, but is sent by the OMS whenever trades occur. To receive *Level2UpdateEvents*, a user must subscribe to *Level2UpdateEvents*.

| Key          | Value                                                        |
| --------------- | ------------------------------------------------------------ |
| MDUpdateID      | **integer**. Market Data Update ID. This sequential ID identifies the order in which the update was created. |
| Number of Unique Accounts | **integer**. Number of accounts that placed orders.  |
| ActionDateTime  | **long integer.**. *ActionDateTime* identifies the time and date that the snapshot was taken or the event occurred, in POSIX format X 1000 (milliseconds since 1 January 1970). |
| ActionType      | **integer**. L2 information provides price data. This value shows whether this data is:<br />**0** new<br />**1** update<br />**2** deletion |
| LastTradePrice  | **real**. The price at which the instrument was last traded. |
| Number of Orders  | **integer**. Number of orders in the GetL2Snapshot.  |
| Price           | **real**. Bid or Ask price for the Quantity (see *Quantity* below). |
| ProductPairCode | **integer**. *ProductPairCode* is the same value and used for the same purpose as *InstrumentID*. The two are completely equivalent. *InstrumentId* 47 = *ProductPairCode* 47. |
| Quantity        | **real**. Quantity available at a given Bid or Ask price (see *Price* above). |
| Side            | **integer**. One of:<br />**0** Buy<br />**1** Sell<br />**2** Short (reserved for future use)<br />**3** Unknown (error condition) |

