## SubscribeLevel2

**Category:** User<br />
**Permissions:** Operator, Trading, Level2MarketData<br />
**Call Type:** Synchronous

Retrieves the latest Level 2 Ticker information and then subscribes the user to Level 2 market data event updates for one specific instrument. Level 2 allows the user to specify the level of market depth information on either side of the bid and ask. The **SubscribeLevel2** call responds with the Level 2 response shown below. The OMS then periodically sends *Level2UpdateEvent* information in the same format as this response until you send the **UnsubscribeLevel2** call.

Only a user with Operator permission can issue a Level2MarketData permission using the call **AddUserMarketDataPermission.**

<aside class="notice"><strong>Note:</strong> <em>Depth</em> in this call is "depth of market," the number of buyers and sellers at greater or lesser prices in the order book for the instrument.</aside>

### Request

```json
{
	"OMSId":  1,
	"InstrumentId": 0
	"Depth":  10 
}
```

>or

```json
{
	"OMSId":  1,
	"Symbol": "BTCUSD"
	"Depth":  10 
}
```

| Key       | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| OMSId        | **integer.** The ID of the Order Management System on which the instrument trades. |
| InstrumentId | **integer.** The ID of the instrument you’re tracking. *Conditionally optional.* |
| Symbol       | **string.** The symbol of the instrument you’re tracking. *Conditionally optional.* |
| Depth        | **integer.** The depth of the order book. The example request returns 10 price levels on each side of the market. |

### Response
```json
[
    [
        0, // MDUpdateId        
        1, // Number of Accounts
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
```
The response is an array of elements for one specific instrument, the number of elements corresponding to the market depth specified in the Request. It is sent as an uncommented, comma-delimited list of numbers. The example is commented.

| Key          | Value                                                        |
| --------------- | ------------------------------------------------------------ |
| MDUpdateID      | **integer**. Market Data Update ID. This sequential ID identifies the order in which the update was created. |
| Number of Accounts        | **integer**. Number of accounts  |
| ActionDateTime  | **long integer.**. *ActionDateTime* identifies the time and date that the snapshot was taken or the event occurred, in POSIX format X 1000 (milliseconds since 1 January 1970). |
| ActionType      | **integer**. L2 information provides price data. This value shows whether this data is:<br />**0** new<br />**1** update<br />**2** deletion |
| LastTradePrice  | **real**. The price at which the instrument was last traded. |
| Number of Orders          | **integer**. Number of orders  |
| Price           | **real**. Bid or Ask price for the Quantity (see *Quantity* below). |
| ProductPairCode | **integer**. *ProductPairCode* is the same value and used for the same purpose as *InstrumentID*. The two are completely equivalent. *InstrumentId* 47 = *ProductPairCode* 47. |
| Quantity        | **real**. Quantity available at a given Bid or Ask price (see *Price* above). |
| Side            | **integer**. One of:<br />**0** Buy<br />**1** Sell<br />**2** Short (reserved for future use)<br />**3** Unknown (error condition) |

