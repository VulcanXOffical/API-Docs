## GetLevel1

**Category:** Trading<br />
**Permissions:** Trading, Public<br />
**Call Type:** Synchronous

Provides a current Level 1 snapshot (best bid, best offer and other data such lasttradedprice) of a specific instrument trading on an Order Management System. The Level 1 snapshot does not allow the user to specify the level of market depth information on either side of the bid and ask.

### Request

```javascript
const { APEX } = require("VulcanX-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise('GetLevel1',{
    OMSId: 1
    InstrumentId: 1
})
```

```http
POST /AP/GetLevel1 HTTP/1.1
Host: hostname goes here...
Content-Type: application/json
Content-Length: 27

{
    "OMSId": 1
    "InstrumentId": 1
}
```

| Key          | Value                                                                                         |
| ------------ | --------------------------------------------------------------------------------------------- |
| OMSId        | **integer.** The ID of the OMS on which the snapshot will be taken._required._                |
| InstrumentId | **integer.** The ID of the instrument whose Level 1 market snapshot will be taken._required._ |

### Response

```json
{
  "OMSId": 1,
  "InstrumentId": 1,
  "BestBid": 28700,
  "BestOffer": 29000,
  "LastTradedPx": 29000,
  "LastTradedQty": 0.001,
  "LastTradeTime": 1679466290437,
  "SessionOpen": 28000,
  "SessionHigh": 29000,
  "SessionLow": 28000,
  "SessionClose": 29000,
  "Volume": 0.001,
  "CurrentDayVolume": 0.222,
  "CurrentDayNotional": 6425.0,
  "CurrentDayNumTrades": 5,
  "CurrentDayPxChange": 1000,
  "Rolling24HrVolume": 0.0,
  "Rolling24HrNotional": 0.0,
  "Rolling24NumTrades": 0,
  "Rolling24HrPxChange": 0,
  "TimeStamp": "1679466290440",
  "BidQty": 0.5,
  "AskQty": 0.5,
  "BidOrderCt": 0,
  "AskOrderCt": 0,
  "Rolling24HrPxChangePercent": 0
}
```

| Key                        | Value                                                                                                                                                                                                                                         |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| OMSId                      | **integer.** The ID of the OMS where the snapshot was taken.                                                                                                                                                                                  |
| InstrumentId               | **integer.** The ID of the instrument (the product pair) whose prices, bids, asks, and volumes are being reported.                                                                                                                            |
| BestBid                    | **real.** The current highest price which a trader currently is willing to buy the instrument (product pair).                                                                                                                                 |
| BestOffer                  | **real.** The lowest price which a trader is willing to sell the instrument for the instrument (product pair).                                                                                                                                |
| Volume                     | **real.** The unit volume of the instrument traded, either during a true session (with a market open and close), or in 24-hour markets, it is the period from UTC Midnight to UTC Midnight, regardless of the nominal location of the market. |
| LastTradedPX               | **real.** The last-traded price for the instrument.                                                                                                                                                                                           |
| LastTradedVolume           | **real.** The last quantity that was traded.                                                                                                                                                                                                  |
| LastTradeTime              | **real.** The last time that the instrument was traded.                                                                                                                                                                                       |
| TimeStamp                  | **real.** The date and time of this snapshot.                                                                                                                                                                                                 |
| BidQty                     | **real.** The quantity currently being bid.                                                                                                                                                                                                   |
| AskQty                     | **real.** The quantity currently being asked.                                                                                                                                                                                                 |
| BidOrderCt                 | **integer.** The count of bid orders.                                                                                                                                                                                                         |
| AskOrderCt                 | **integer.** The count of ask orders.                                                                                                                                                                                                         |
| SessionOpen                | **real.** Opening price. In markets with openings and closings, this is the opening price for the current session; in 24-hour markets, it is the price as of UTC Midnight beginning the current day.                                          |
| SessionHigh                | **real.** Highest price during the trading day, either during a true session (openings and closings) or UTC Midnight to UTC Midnight.                                                                                                         |
| SessionLow                 | **real.** Lowest price during the trading day, either during a true session (openings and closings) or UTC Midnight to UTC Midnight.                                                                                                          |
| SessionClose               | **real.** The closing price. In markets that open and close, this is the closing price for the current or most recent session; for 24-hour markets, it is the price as of the most recent UTC Midnight.                                       |
| CurrentDayVolume           | **real.** The unit volume of the instrument that is the subject of the snapshot, either during a true session (openings and closings) or in 24-hour markets, during the period UTC Midnight to UTC Midnight.                                  |
| CurrentDayNumTrades        | **integer.** The number of trades during the current day, either during a true session (openings and closings) or in a 24-hour market the period from UTC Midnight to UTC Midnight.                                                           |
| CurrentDayPxChange         | **real.** Change in price over the current session or from UTC Midnight to UTC Midnight.                                                                                                                                                      |
| CurrentNotional            | **decimal.** Current day quote volume - resets at UTC Midnight.                                                                                                                                                                               |
| Rolling24HrNotional        | **decimal.** Rolling 24 hours quote volume.                                                                                                                                                                                                   |
| Rolling24HrVolume          | **real.** Unit volume of the instrument over the past 24 hours, regardless of time zone. This value recalculates continuously.                                                                                                                |
| Rolling24HrNumTrades       | **real.** Number of trades during the past 24 hours, regardless of time zone. This value recalculates continuously.                                                                                                                           |
| Rolling24HrPxChange        | **real.** Price change during the past 24 hours, regardless of time zone. This value recalculates continuously.                                                                                                                               |
| Rolling24HrPxChangePercent | **real.** Percent change in price during the past 24 hours.                                                                                                                                                                                   |
