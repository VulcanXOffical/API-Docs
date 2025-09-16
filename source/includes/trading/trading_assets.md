## Assets

**Category:** Trading<br />
**Permissions:** Public<br />
**Call Type:** Synchronous

The assets endpoint is to provide a detailed summary for each currency available on the exchange for CMC Integration

### Request

No field is required in the request payload.

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("Assets", {});
```

```http
POST /AP/Assets HTTP/1.1
Host: hostname goes here...

```

### Response

The response returns an array of objects, each object is for a specific asset in the exchange. Each field in the object is labeled as to what it means.

```javascript
[
  {
    name: "Bitcoin",
    unified_cryptoasset_id: 1,
    min_withdraw: 0.00000001,
  },
  {
    name: "TBTC",
    unified_cryptoasset_id: 5776,
    min_withdraw: 0.00000001,
  },
  {
    name: "Ethereum Kovan",
    unified_cryptoasset_id: 1027,
    min_withdraw: 0.00000001,
  },
  {
    name: "Chainlink",
    unified_cryptoasset_id: 1975,
    min_withdraw: 0.00000001,
  },
  {
    name: "ICON",
    unified_cryptoasset_id: 2099,
    min_withdraw: 0.00000001,
  },
  {
    name: "Dogecoin",
    unified_cryptoasset_id: 74,
    min_withdraw: 0.00000001,
  },
  {
    name: "Thai Baht",
    unified_cryptoasset_id: 21430,
    min_withdraw: 0.00000001,
  },
  {
    name: "Tether",
    unified_cryptoasset_id: 825,
    min_withdraw: 0.00000001,
  },
  {
    name: "USD  Coin",
    unified_cryptoasset_id: 3408,
    min_withdraw: 0.00000001,
  },
];
```

```http
[
    {
        "name": "Bitcoin",
        "unified_cryptoasset_id": 1,
        "min_withdraw": 0.0000000100000000000000000000
    },
    {
        "name": "TBTC",
        "unified_cryptoasset_id": 5776,
        "min_withdraw": 0.0000000100000000000000000000
    },
    {
        "name": "Ethereum Kovan",
        "unified_cryptoasset_id": 1027,
        "min_withdraw": 0.0000000100000000000000000000
    },
    {
        "name": "Chainlink",
        "unified_cryptoasset_id": 1975,
        "min_withdraw": 0.0000000100000000000000000000
    },
    {
        "name": "ICON",
        "unified_cryptoasset_id": 2099,
        "min_withdraw": 0.0000000100000000000000000000
    },
    {
        "name": "Dogecoin",
        "unified_cryptoasset_id": 74,
        "min_withdraw": 0.0000000100000000000000000000
    },
    {
        "name": "Tether",
        "unified_cryptoasset_id": 825,
        "min_withdraw": 0.0000000100000000000000000000
    },
    {
        "name": "USD  Coin",
        "unified_cryptoasset_id": 3408,
        "min_withdraw": 0.0000000100000000000000000000
    }
]
```
