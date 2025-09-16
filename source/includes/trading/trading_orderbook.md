## OrderBook

**Category:** Trading<br />
**Permissions:** Public<br />
**Call Type:** Synchronous

The OrderBook endpoint is to provide a complete level 2 order book (arranged by best asks/bids) with full depth returned for a given market pair for CMC integration. Parameters can also be supplied in the request payload.

### Request

| Key         | Value                                                                                                                                                                                                                                                                                                                                                    |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Market_Pair | The instrument symbol, instrument id is not accepted. _required_                                                                                                                                                                                                                                                                                         |
| Depth       | Depth of the orderbook you want to see, this only applicable if **Level** parameter is set to 2. Depth will always be 1 if this is not set or if Level is set to 1._optional_                                                                                                                                                                            |
| Level       | Either 1 or 2. 1 mean you only want to see the best bid and best ask, 2 means you want to see other levels of the book, number of bids and ask you will see depends on the **Depth** set, if **Depth** is not set and **Level** is set to 2, best bid and best ask will only be the ones to be returned.If **Level** is not set, default is 1._optional_ |

```javascript
const { APEX } = require("VulcanX-apex-api");
const apex = new APEX("websocket url goes here...");

//No need to set Depth if Level is set to 1
await apex.RPCPromise("OrderBook", {
  Market_Pair: "BTCUSD",
  Level: 1,
});

//Level 2, you need to set Depth to a number higher than 1 else you will only see best bid and best ask
await apex.RPCPromise("OrderBook", {
  Market_Pair: "BTCUSD",
  Depth: 10,
  Level: 2,
});
```

```http
POST /AP/OrderBook HTTP/1.1
Host: hostname goes here...
Content-Type: application/json
Content-Length: 52

//No need to set Depth if Level is set to 1
{
    "Market_Pair": "BTCUSD",
    "Level": 1
}

////Level 2, you need to set Depth to a number higher than 1 else you will only see best bid and best ask
{
Market_Pair: "BTCUSD",
Depth: 10,
Level: 2,
}
```

### Response

```javascript
//Level 1
{
    "timestamp": 1679548364728,
    "bids": [
        [
            2, //Quantity
            28900 //Price
        ]
    ],
    "asks": [
        [
            0.5, //Quantity
            29000 //Price
        ]
    ]
}

//level 2, Depth 10, only 2 bids existing, only 1 ask existing
{
    "timestamp": 1679548299447,
    "bids": [
        [
            2, //Quantity
            28900 //Price
        ],
        [
            1,
            28700
        ]
    ],
    "asks": [
        [
            0.5,
            29000
        ]
    ]
}
```

```http
//Level 1
{
    "timestamp": 1679548364728,
    "bids": [
        [
            2, //Quantity
            28900 //Price
        ]
    ],
    "asks": [
        [
            0.5,
            29000
        ]
    ]
}

//level 2, Depth 10, only 2 bids existing, only 1 ask existing
{
    "timestamp": 1679548299447,
    "bids": [
        [
            2, //Quantity
            28900 //Price
        ],
        [
            1,
            28700
        ]
    ],
    "asks": [
        [
            0.5,
            29000
        ]
    ]
}
```

Returns a JSON object with fields timestamp, bids and asks.

| Key       | Value                                                                                               |
| --------- | --------------------------------------------------------------------------------------------------- |
| timestamp | Unix timestamp in milliseconds, equivalent to the current timestamp when the response was returned. |
| bids      | The quantity and price per level which someone is willing to buy.                                   |
| asks      | The quantity and price per level which someone is willing sell.                                     |
