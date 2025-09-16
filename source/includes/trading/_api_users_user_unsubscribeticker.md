## UnsubscribeTicker

**Category:** Trading<br />
**Permissions:** Operator, Trading, Level1MarketData, Public(If Market Data is not Permissioned)<br />
**Call Type:** Synchronous

Unsubscribes the user from a Ticker Market Data Feed.

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.UnSubscribeTicker({
  OMSId: 1,
  InstrumentId: 1,
});
```

```http
<!---UnSubscribeTicker is not available in http. Subscription APIs are only supported in websockets.-->

```

| Key          | Value                                                                                                             |
| ------------ | ----------------------------------------------------------------------------------------------------------------- |
| OMSId        | **integer.** The ID of the Order Management System on which the user has subscribed to a ticker market data feed. |
| InstrumentId | **long integer.** The ID of the instrument being tracked by the ticker market data feed.                          |

### Response

```javascript
{
  "result": true,
  "errormsg": null,
  "errorcode": 0,
  "detail": null
}
```

```http
<!---UnSubscribeTicker is not available in http. Subscription APIs are only supported in websockets.-->

```

| Key       | Value                                                                                                                                                                                                                                                                                                                                                           |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result    | **Boolean.** A successful receipt of the unsubscribe request returns _true_; and unsuccessful receipt (an error condition) returns _false_.                                                                                                                                                                                                                     |
| errormsg  | **string.** A successful receipt of the unsubscribe request returns _null_; the _errormsg_ parameter for an unsuccessful request returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104) |
| errorcode | **integer.** A successful receipt of the unsubscribe request returns 0. An unsuccessful receipt returns one of the _errorcodes_ shown in the _errormsg_ list.                                                                                                                                                                                                   |
| detail    | **string.** Message text that the system may send. Usually _null_.                                                                                                                                                                                                                                                                                              |
