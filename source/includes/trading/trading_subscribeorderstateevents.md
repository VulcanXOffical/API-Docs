## SubscribeOrderStateEvents

**Category:** Trading<br />
**Permissions:** Trading<br />
**Call Type:** Synchronous

Subscribe to order state events of a specific account's orders. Optional parameter to filter by instrument.

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("SubscribeOrderStateEvents", {
  OMSId: 1,
  AccountId: 1,
  InstrumentId: 1, //optional to filter for a specific instrument
});
```

```http
//SubscribeOrderStateEvents is not available in HTTP. Subscription APIs is not supported in HTTP.
```

| Key          | Value                                                                                                                           |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------- |
| OMSId        | **integer.** The ID of the OMS on which the snapshot of all instruments will be taken._required._                               |
| AccountId    | **integer.** The ID of the account to subscribe with._required._                                                                |
| InstrumentId | **integer.** The ID of the instrument to subscribe orderstateevents with. This field serves as the filter parameter._optional._ |

### Response

```javascript
{
  Subscribed: true;
}
```

```http
//SubscribeOrderStateEvents is not available in HTTP. Subscription APIs is not supported in HTTP.
```

Returns either Subscribed: true or false. If false, it means that you were not able to subscribe to orderstateevents of the account. After successfully subscribing to orderstatevents of the account, you will receive the events message for any change of state of the account's order/s.
