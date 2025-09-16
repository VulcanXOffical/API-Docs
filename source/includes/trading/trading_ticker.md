## Ticker

**Category:** Trading<br />
**Permissions:** Public<br />
**Call Type:** Synchronous

Ticker endpoint provide a 24-hour pricing and volume summary for each market pair and each market type (spot, perpetuals, physical futures, options) available on the exchange for CMC integration.

### Request

No field is required in the request payload.

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("Ticker", {});
```

```http
POST /AP/Ticker HTTP/1.1
Host: hostname goes here...

```

### Response

```javascript
{
    "BTC_USD": {
        "base_id": 1,
        "quote_id": 0,
        "last_price": 29000,
        "base_volume": 0.2220000000000000000000000000,
        "quote_volume": 6425.0000000000000000000000000
    },
    "ETH_USD": {
        "base_id": 1027,
        "quote_id": 0,
        "last_price": 1970,
        "base_volume": 0.000,
        "quote_volume": 0.000
    }
}
```

```http
{
    "BTC_USD": {
        "base_id": 1,
        "quote_id": 0,
        "last_price": 29000,
        "base_volume": 0.2220000000000000000000000000,
        "quote_volume": 6425.0000000000000000000000000
    },
    "ETH_USD": {
        "base_id": 1027,
        "quote_id": 0,
        "last_price": 1970,
        "base_volume": 0.000,
        "quote_volume": 0.000
    }
}
```

Returns a JSON object, each field in the object represents an instrument in the exchange. Each field in the object has their properties and are labeled as to what they mean.
