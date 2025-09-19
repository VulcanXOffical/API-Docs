## SubscribeLevel1

**Category:** Trading<br />
**Permissions:** Operator, Trading, Level1MarketData, Public(If Market Data is not Permissioned)<br />
**Call Type:** Synchronous

Retrieves the latest Level 1 Ticker information and then subscribes the user to ongoing Level 1 market data event updates for one specific instrument.

The **SubscribeLevel1** call responds with the Level 1 response shown below. The OMS then periodically sends in the same format as this response _Leve1UpdateEvent_ information when best-bid/best-offer issue, until you send the **UnsubscribeLevel1** call.

Only a user with Operator permission can issue Level1MarketData permission using the call **\*AddUserMarketDataPermission.**

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.SubscribeLevel1({
  OMSId: 1,
  InstrumentId: 1,
});

//Instrument can also be identified via its symbol e.g. BTCUSD
await apex.SubscribeLevel1({
  OMSId: 1,
  Symbol: "BTCUSD",
});
```

```http
<!---SubscribeLevel1 is not available in http. Subscription APIs are only supported in websockets.-->

```

| Key          | Value                                                                                                         |
| ------------ | ------------------------------------------------------------------------------------------------------------- |
| OMSId        | **integer**. The ID of the Order Management System on which the instrument trades._required_                  |
| InstrumentId | **integer**. The ID of the instrument you’re tracking. _required_                                             |
| Symbol       | **string**. Can be used instead of the InstrumentId. The symbol of the instrument you’re tracking. _required_ |

### Response

The **SubscribeLevel1** response and _Level1UpdateEvent_ both provide the same information.

```javascript
{
  "OMSId": 1,
  "InstrumentId": 1,
  "BestBid": 6423.57,
  "BestOffer": 6436.53,
  "LastTradedPx": 6423.57,
  "LastTradedQty": 0.96183964,
  "LastTradeTime": 1534862990343,
  "SessionOpen": 6249.64,
  "SessionHigh": 11111,
  "SessionLow": 4433,
  "SessionClose": 6249.64,
  "Volume": 0.96183964,
  "CurrentDayVolume": 3516.31668185,
  "CurrentDayNumTrades": 8529,
  "CurrentDayPxChange": 173.93,
  "CurrentNotional": 0.0,
  "Rolling24HrNotional": 0.0,
  "Rolling24HrVolume": 4319.63870783,
  "Rolling24NumTrades": 10585,
  "Rolling24HrPxChange": -0.4165607307408487,
  "TimeStamp": "1534862990358"
}
```

| Key                  | Value                                                                                                                                                                             |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| OMSId                | **integer**. The ID of the Order Management System on which the instrument trades.                                                                                                |
| InstrumentId         | **integer**. The ID of the instrument being tracked.                                                                                                                              |
| BestBid              | **real**. The current best bid for the instrument.                                                                                                                                |
| BestOffer            | **real**. The current best offer for the instrument.                                                                                                                              |
| LastTradedPx         | **real**. The last-traded price for the instrument.                                                                                                                               |
| LastTradedQty        | **real**. The last-traded quantity for the instrument.                                                                                                                            |
| LastTradeTime        | **long integer**. The time of the last trade, in POSIX format.                                                                                                                    |
| SessionOpen          | **real**. Opening price. In markets with openings and closings, this is the opening price for the current session; in 24-hour markets, it is the price as of UTC Midnight.        |
| SessionHigh          | **real**. Highest price during the trading day, either during a session with opening and closing prices or UTC midnight to UTC midnight.                                          |
| SessionLow           | **real**. Lowest price during the trading day, either during a session with opening and closing prices or UTC midnight to UTC midnight.                                           |
| SessionClose         | **real**. The closing price. In markets with openings and closings, this is the closing price for the current session; in 24-hour markets, it is the price as of UTC Midnight.    |
| Volume               | **real**. The last-traded quantity for the instrument, same value as LastTradedQty                                                                                                |
| CurrentDayVolume     | **real**. The unit volume of the instrument traded either during a session with openings and closings or in 24-hour markets, the period from UTC Midnight to UTC Midnight.        |
| CurrentDayNumTrades  | **integer**. The number of trades during the current day, either during a session with openings and closings or in 24-hour markets, the period from UTC Midnight to UTC Midnight. |
| CurrentDayPxChange   | **real**. Current day price change, either during a trading session or UTC Midnight to UTC midnight.                                                                              |
| CurrentNotional      | **decimal.** Current day quote volume - resets at UTC Midnight.                                                                                                                   |
| Rolling24HrNotional  | **decimal.** Rolling 24 hours quote volume.                                                                                                                                       |
| Rolling24HrVolume    | **real**. Unit volume of the instrument during the past 24 hours, regardless of time zone. Recalculates continuously.                                                             |
| Rolling24HrNumTrades | **integer**. Number of trades during the past 24 hours, regardless of time zone. Recalculates continuously.                                                                       |
| Rolling24HrPxChange  | **real**. Price change during the past 24 hours, regardless of time zone. Recalculates continuously.                                                                              |
| TimeStamp            | **long integer**. The time this information was provided, in POSIX format.                                                                                                        |
