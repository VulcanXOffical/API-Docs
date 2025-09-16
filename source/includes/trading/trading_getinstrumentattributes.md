## GetInstrumentAttributes

**Category:** Trading<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

Get attributes of a specific instrument.

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("GetInstrumentAttributes", {
  OMSId: 1,
  InstrumentId: 1,
});
```

```http
POST /AP/GetInstrumentAttributes HTTP/1.1
Host: hostname goes here...
aptoken: d0260e4b-bf6e-4fcd-a8cd-ad1cb01f2235 //valid sessiontoken
Content-Type: application/json
Content-Length: 44

{
    "OMSId": 1,
    "InstrumentId": 1
}
```

| Key          | Value                                                                                 |
| ------------ | ------------------------------------------------------------------------------------- |
| OMSId        | **integer** The Id of the OMS where the instrument belongs._required._                |
| InstrumentId | **integer**. The Id of the instrument which you want to get attributes of._required._ |

### Response

```json
[
  {
    "OMSId": 1,
    "InstrumentId": 1,
    "KeyName": "Crypto",
    "KeyValue": "true"
  }
]
```

The response is an array of objects, each object represents an instrument attribute in key-value pair.

| Key          | Value                                                              |
| ------------ | ------------------------------------------------------------------ |
| OMSId        | **integer**. Id of the OMS where the instrument belongs.           |
| InstrumentId | **integer**. Id of the instrument whose attribute/s were returned. |
| KeyName      | **string**. The instrument attribute keyname.                      |
| KeyValue     | **string**. The instrument attribute keyvalue.                     |
