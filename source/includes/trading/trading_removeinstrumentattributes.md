## RemoveInstrumentAttributes

**Category:** Trading<br />
**Permissions:** Operator<br />
**Call Type:** Synchronous

Removes an instrument attribute based on the the KeyValue provided.

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("RemoveInstrumentAttributes", {
  OMSId: 1,
  InstrumentId: 1,
  KeyName: "AnotherKey",
});
```

```http
POST /AP/RemoveInstrumentAttributes HTTP/1.1
Host: hostname goes here...
aptoken: d0260e4b-bf6e-4fcd-a8cd-ad1cb01f2235 //valid sessiontoken
Content-Type: application/json
Content-Length: 74

{
    "OMSId": 1,
    "InstrumentId": 1,
    "KeyName": "AnotherKey"
}
```

| Key          | Value                                                                                    |
| ------------ | ---------------------------------------------------------------------------------------- |
| OMSId        | **integer** The Id of the OMS where the instrument belongs._required._                   |
| InstrumentId | **integer**. The Id of the instrument which you want to add an attribute for._required._ |
| KeyName      | **string** The instrument attribute keyname to be set._required._                        |

### Response

```json
{
  "result": true,
  "errormsg": null,
  "errorcode": 0,
  "detail": null
}
```

| Key       | Value                                                                                                                                                                                                                                                                                                                             |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result    | **Boolean**. A successful receipt of the cancellation returns true; and unsuccessful receipt of the cancellation (an error condition) returns false.                                                                                                                                                                              |
| errormsg  | **string**. A successful receipt of the cancellation returns null; the _errormsg_ parameter for an unsuccessful receipt returns one of the following messages: Not Authorized (errorcode 20), Invalid Request (errorcode 100), Operation Failed (errorcode 101), Server Error (errorcode 102), Resource Not Found (errorcode 104) |
| errorcode | **integer**. A successful receipt of the cancellation returns 0. An unsuccessful receipt returns one of the _errorcodes_ shown in the _errormsg_ list.                                                                                                                                                                            |
| detail    | **string**. Message text that the system may send. Usually _null_.                                                                                                                                                                                                                                                                |
