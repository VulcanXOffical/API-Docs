## Summary

**Category:** Trading<br />
**Permissions:** Public<br />
**Call Type:** Synchronous

Returns the summary for each instrument present in the exchange. Summary data is technically a simplified Level1 data.

### Request

No field is required in the request payload.

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("Summary", {});
```

```http
POST /AP/Summary HTTP/1.1
Host: hostname goes here...

```

### Response

The response returns an array of objects, each object is for a specific pair or instrument in the exchange.

```javascript
[
  {
    trading_pairs: "BTC_USD",
    last_price: 29000,
    lowest_ask: 29000,
    highest_bid: 28700,
    base_volume: 0.222,
    quote_volume: 6425.0,
    price_change_percent_24h: 3.57142857142857142857142857,
    highest_price_24h: 29000,
    lowest_price_24h: 28000,
  },
  {
    trading_pairs: "ETH_USD",
    last_price: 1970,
    lowest_ask: 0,
    highest_bid: 0,
    base_volume: 0.0,
    quote_volume: 0.0,
    price_change_percent_24h: 0,
    highest_price_24h: 0,
    lowest_price_24h: 0,
  },
];
```

```http
[
    {
        "trading_pairs": "BTC_USD",
        "last_price": 29000,
        "lowest_ask": 29000,
        "highest_bid": 28700,
        "base_volume": 0.2220000000000000000000000000,
        "quote_volume": 6425.0000000000000000000000000,
        "price_change_percent_24h": 3.5714285714285714285714285700,
        "highest_price_24h": 29000,
        "lowest_price_24h": 28000
    },
    {
        "trading_pairs": "ETH_USD",
        "last_price": 1970,
        "lowest_ask": 0,
        "highest_bid": 0,
        "base_volume": 0.000,
        "quote_volume": 0.000,
        "price_change_percent_24h": 0,
        "highest_price_24h": 0,
        "lowest_price_24h": 0
    }
 ]

```
