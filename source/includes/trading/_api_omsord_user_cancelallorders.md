## CancelAllOrders

**Category:** Trading<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

Cancels all open matching orders for the specified account on an Order Management System.

A user with Trading permission can cancel orders for accounts it is associated with; a user with Operator permissions can cancel orders for any aaccount.

<aside class="warning"><strong>Warning:</strong> <strong>CancelAllOrders</strong> will cancel all existing orders on an OMS when sending AccountID = 0 or when AccountID is ommited.</aside>

<aside class="notice"><strong>Note:</strong> Multiple users may have access to the same account.</aside>

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

//Cancel all orders of a specific account for a specific instrument
await apex.RPCPromise("CancelAllOrders", {
  OMSId: 1,
  AccountId: 9,
  InstrumentId: 1,
});

//Cancel all orders of all accounts for a specific instrument
await apex.RPCPromise("CancelAllOrders", {
  OMSId: 1,
  AccountId: 0,
  InstrumentId: 1,
});

//Cancel all orders of all accounts for all instruments
await apex.RPCPromise("CancelAllOrders", {
  OMSId: 1,
  AccountId: 0,
  InstrumentId: 0,
});
```

```http
POST /AP/CancelAllOrders HTTP/1.1
Host: hostname goes here...
aptoken: 0b9e03f8-40c8-4653-b52f-1e75e9f9cd0b //valid sessiontoken
Content-Type: application/json
Content-Length: 60

//Cancel all orders of a specific account for a specific instrument
{
  "OMSId": 1,
  "AccountId": 9,
  "InstrumentId": 1
}

//Cancel all orders of all accounts for a specific instrument
{
  "OMSId": 1,
  "AccountId": 0,
  "InstrumentId": 1
}

//Cancel all orders of all accounts for all instruments
{
  "OMSId": 1,
  "AccountId": 0,
  "InstrumentId": 0
}
```

| Key         | Value                                                                                                                                                                  |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AccountId   | **integer.** The account for which all orders are being canceled. If no AccountId is defined, orders for all accounts will be cancelled. _optional._                   |
| OMSId       | **integer.** The Order Management System under which the account operates. _required_.                                                                                 |
| IntrumentId | **integer.** The instrument for which all orders are being canceled. If there is no instrumentid defined, all orders for all instruments will be cancelled._optional._ |

### Response

```javascript
{
  "result": true,
  "errormsg": "",
  "errorcode": 0,
  "detail": ""
}
```

```http
{
  "result": true,
  "errormsg": "",
  "errorcode": 0,
  "detail": ""
}
```

The Response is a standard response object.

| Key       | Value                                                                                                                                                                                                                                                                                                                                                                                 |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result    | **Boolean.** If the call has been successfully received by the Order Management System, _result_ is _true;_ otherwise it is _false._                                                                                                                                                                                                                                                  |
| errormsg  | **string.** A successful receipt of the call returns _null._ The _errormsg_ key for an unsuccessful call returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer.** A successful receipt of the call returns 0. An unsuccessful receipt of the call returns one of the _errorcodes_ shown in the _errormsg_ list.                                                                                                                                                                                                                            |
| detail    | **string.** Message text that the system may send.                                                                                                                                                                                                                                                                                                                                    |
