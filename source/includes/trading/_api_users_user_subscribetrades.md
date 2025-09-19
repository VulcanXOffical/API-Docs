## SubscribeTrades

**Category:** Trading<br />
**Permissions:** Operator, Trading, Level1MarketData, Public(If Market Data is not Permissioned)<br />
**Call Type:** Synchronous

Subscribes an authenticated user to the Trades Market Data Feed for a specific instrument. Each trade has two sides: _Buy_ and _Sell_.

**SubscribeTrades** returns the response documented here for your immediate information, then periodically sends the _OrderTradeEvent_ documented in **SubscribeAccountEvents.**

Only a user with Operator permission can issue the permission Level1MarketData using the call **AddUserMarketDataPermission.**

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.SubscribeTrades({
  OMSId: 1,
  InstrumentId: 1,
  IncludeLastCount: 10,
});
```

```http
<!---SubscribeTrades is not available in http. Subscription APIs are only supported in websockets.-->

```

| Key              | Value                                                                                                  |
| ---------------- | ------------------------------------------------------------------------------------------------------ |
| OMSId            | **integer**. The ID of the Order Management System on which the instrument is traded._required._       |
| InstrumentId     | **long integer**. The ID of the instrument whose trades will be reported._required._                   |
| IncludeLastCount | **integer**. Specifies the number of previous trades to retrieve in the immediate snapshot._required._ |

### Response

> Numerical keys reduce package transmission load. See Response table for an explanation.

```javascript
[
  {
    0: 1713390,
    1: 1,
    2: 0.25643269,
    3: 6419.77,
    4: 203100209,
    5: 203101083,
    6: 1534863265752,
    7: 2,
    8: 1,
    9: 0,
    10: 0,
  },
];
```

```http
<!---SubscribeTrades is not available in http. Subscription APIs are only supported in websockets.-->

```

The response returns an array of trades. The keys of each trade are numbers to reduce payload traffic.

| Key                                   | Value                                                                                                                                                                                                                                                                                                  |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 0 (TradeId)                           | **integer.** The ID of this trade.                                                                                                                                                                                                                                                                     |
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
