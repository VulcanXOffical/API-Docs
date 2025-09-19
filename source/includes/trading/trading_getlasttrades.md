## GetLastTrades

**Category:** Trading<br />
**Permissions:** Public, Trading<br />
**Call Type:** Synchronous

Gets the trades that happened for a specific instrument, parameter **Count** can be set to limit the results.

### Request

| Key          | Value                                                                                                                                                                                      |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| InstrumentId | The id of the instrument, symbol is not accepted.If you don't specify this, response will have the current timestamp which is not valid._required_                                         |
| OMSId        | ID of the OMS where the pair or instrument is being traded._required_                                                                                                                      |
| Count        | Value represents the number of trades you want to get, value of 10 will return 10 most recent trades. If not set, all trades for the instrument will be included in the results._optional_ |

```javascript
const { APEX } = require("VulcanX-apex-api");
const apex = new APEX("websocket url goes here...");

//Get all trades for instrument id 1
await apex.RPCPromise("GetLastTrades", {
  InstrumentId: 1,
  OMSId: 1,
});

//Get the 10 most recent trades for instrumentid 1
await apex.RPCPromise("GetLastTrades", {
  InstrumentId: 1,
  OMSId: 1,
  Count: 10,
});
```

```http
POST /AP/GetLastTrades HTTP/1.1
Host: hostname goes here...
Content-Type: application/json
Content-Length: 48

//Get all trades for instrument id 1
{
    "OMSId": 1,
    "InstrumentId": 1
}

//Get the 10 most recent trades for instrumentid 1
{
    "OMSId": 1,
    "InstrumentId": 1,
    "Count": 10
}
```

### Response

The response returns an object with multiple arrays, each array represents 1 trade.

| Key                                   | Value                                                                                                                                                                                                                                                                                                  |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 0                                     | **integer.** .                                                                                                                                                                                                                                                                                         |
| 1 (ProductPairCode)                   | **integer.** _ProductPairCode_ is the same number and used for the same purpose as _InstrumentID_. The two are completely equivalent in value. InstrumentId 47 = ProductPairCode 47.                                                                                                                   |
| 2 (Quantity)                          | **real.** The quantity of the instrument traded.                                                                                                                                                                                                                                                       |
| 3 (Price)                             | **real.** The price at which the instrument traded.                                                                                                                                                                                                                                                    |
| 4 (Order1)                            | **integer.** The ID of the first order that resulted in the trade, either Buy or Sell.                                                                                                                                                                                                                 |
| 5 (Order2)                            | **integer.** The ID of the second order that resulted in the trade, either Buy or Sell.                                                                                                                                                                                                                |
| 6 (Tradetime)                         | **long integer.** UTC trade time in Total Milliseconds. POSIX format.                                                                                                                                                                                                                                  |
| 7 (Direction)                         | **integer.** Effect of the trade on the instrument’s market price. One of:<br />0 NoChange<br />1 UpTick<br />2 DownTick                                                                                                                                                                               |
| 8 (TakerSide)                         | **integer.** Which side of the trade took liquidity? One of:<br />0 Buy<br />1 Sell<br /><br />The maker side of the trade provides liquidity by placing the order on the book (this can be a buy or a sell order). The other, taker, side takes the liquidity. It, too, can be buy-side or sell-side. |
| 9 (BlockTrade)                        | **Boolean.** Was this a privately negotiated trade that was reported to the OMS? A private trade returns 1 (_true_); otherwise 0 (_false_). Default is _false_. Block trades are not supported in exchange version 3.1                                                                                 |
| 10 (order1ClientId or order2ClientId) | **integer.** The client-supplied order ID for the trade. Internal logic determines whether the program reports the _order1ClientId_ or the _order2ClientId_.                                                                                                                                           |

```javascript
[
  [14, 2, 0.02, 1970, 5922, 5923, 1675332676849, 1, 0, 0, 0],
  [15, 2, 0.98, 1970, 5922, 6012, 1676397856371, 0, 0, 0, 0],
];
```

```http
[
    [
        14,
        2,
        0.02,
        1970,
        5922,
        5923,
        1675332676849,
        1,
        0,
        0,
        0
    ],
    [
        15,
        2,
        0.98,
        1970,
        5922,
        6012,
        1676397856371,
        0,
        0,
        0,
        0
    ]
]
```
