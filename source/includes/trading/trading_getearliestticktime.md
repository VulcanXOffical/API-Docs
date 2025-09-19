## GetEarliestTickTime

**Category:** Trading<br />
**Permissions:** Level1MarketData, Operator<br />
**Call Type:** Synchronous

Gets the earliest ticker time possible for a specific instrument or market pair.

### Request

| Key          | Value                                                                                                                                              |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| InstrumentId | The id of the instrument, symbol is not accepted.If you don't specify this, response will have the current timestamp which is not valid._required_ |
| OMSId        | ID of the OMS where the pair or instrument is being traded._required_                                                                              |

```javascript
const { APEX } = require("VulcanX-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("GetEarliestTickTime", {
  InstrumentId: 1,
  OMSId: 1,
});
```

```http
POST /AP/GetEarliestTickTime HTTP/1.1
Host: hostname goes here..
Content-Type: application/json
aptoken: 239260f0-dd79-439b-85e2-a5a24fcd9158 //valid session token, can be acquired during HTTP authentication
Content-Length: 54

{
    "OMSId": 1,
    "InstrumentId": 1

}
```

### Response

The response returns an array with one element.

| Key   | Value                                                                                                                         |
| ----- | ----------------------------------------------------------------------------------------------------------------------------- |
| nokey | Unix timestamp in milliseconds, equivalent to the timestamp when the instrument was traded for the first time in the exchange |

```javascript
[1651148820000];
```

```http
[
    1651148820000
]
```
