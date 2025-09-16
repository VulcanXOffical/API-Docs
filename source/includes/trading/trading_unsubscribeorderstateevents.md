## UnSubscribeOrderStateEvents

**Category:** Trading<br />
**Permissions:** Trading<br />
**Call Type:** Synchronous

UnSubscribe from account-level events. After being unsubscribed, you will stop receiving real-time events about transactions that concerns the specific account you unsubscribed to.

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise('UnSubscribeOrderStateEvents',{
    OMSId: 1,
    AccountId: 1
    InstrumentId: 1 //Optional to unsubscribe to a specific instrument only
})
```

```http
//UnSubscribeOrderStateEvents is not available in HTTP. Subscription APIs is not supported in HTTP.
```

| Key          | Value                                                                                                                               |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------- |
| OMSId        | **integer.** The ID of the OMS on which the snapshot of all instruments will be taken._required._                                   |
| AccountId    | **integer.** The ID of the account to subscribe with. This to make sure you will be unsubscribed to the correct account._required._ |
| InstrumentId | **integer.** The ID of the instrument to unsubscribe orderstateevents with. This field serves as the filter parameter._optional._   |

### Response

```javascript
{
  UnSubscribed: true;
}
```

```http
//UnSubscribeOrderStateEvents is not available in HTTP. Subscription APIs is not supported in HTTP.
```
