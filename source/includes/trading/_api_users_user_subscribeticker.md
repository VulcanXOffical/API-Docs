## SubscribeTicker

**Category:** Trading<br />
**Permissions:** Operator, Trading, Level1MarketData, Public(If Market Data is not Permissioned)<br />
**Call Type:** Synchronous

Subscribes a user to a Ticker Market Data Feed for a specific instrument and interval. **SubscribeTicker** sends a response object as described below, and then periodically returns a _TickerDataUpdateEvent_ that matches the content of the response object.

Only a user with Operator permission can issue a Level1MarketData permission using the call **AddUserMarketDataPermission.**

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.SubscribeTicker({
  OMSId: 1,
  InstrumentId: 1,
  Interval: 60,
  IncludeLastCount: 10,
});
```

```http
<!---SubscribeTicker is not available in http. Subscription APIs are only supported in websockets.-->

```

| Key              | Value                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------ |
| OMSId            | **integer.** The ID of the Order Management System._required._                             |
| InstrumentId     | **long integer.** The ID of the instrument whose ticker data you want to track._required._ |
| Interval         | **integer.** Specifies in seconds how frequently to obtain ticker updates._required._      |
| IncludeLastCount | **integer.** The limit of records returned in the ticker history._required._               |

### Response

```javascript

[
  [1501603632000, //DateTime - UTC - Milliseconds since 1/1/1970
   2700.33, //High
   2701.2687.01, //Low
   2687.01, //Open
   2687.01, //Close
   24.86100992, //Volume
   0, //Inside Bid Price
   2870.95, //Inside Ask Price
   1], //InstrumentId
]
```

```http
<!---SubscribeTicker is not available in http. Subscription APIs are only supported in websockets.-->

```

The response returns an array of objects , each object an unlabeled, comma-delimited array of numbers. The Open price and Close price are those at the beginning of the tick — the Interval time subscribed to in the request. For 24-hour exchanges, the trading day runs from UTC midnight to UTC midnight; highs, lows, opens, closes, and volumes consider that midnight-to-midnight period to be the trading day. The data order is:

- date/time UTC in milliseconds since 1/1/1970
- high
- low
- open
- close
- volume
- inside bid price
- inside ask price
- instrument ID
