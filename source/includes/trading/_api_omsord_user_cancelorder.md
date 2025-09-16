## CancelOrder

**Category:** Trading<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

Cancels a specific open order that has been placed but has not yet been fully executed. Only cancels one order at a time specific to the orderid defined in the request.

A user with Trading permission can cancel an order only for an account it is associated with; a user with Operator permission can cancel an order for any account.

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");
await apex.RPCPromise("CancelOrder", {
  OMSId: 1,
  AccountId: 9,
  OrderId: 6500,
});
```

```http
POST /AP/CancelOrder HTTP/1.1
Host: hostname goes here...
aptoken: 604f9459-163f-4114-8ecc-928597554747
Content-Type: application/json
Content-Length: 57

{
  "OMSId": 1,
  "OrderId": 6500,
  "AccountId": 9
}
```

The OMS ID and the Order ID precisely identify the order you wish to cancel, the Order ID is unique across an OMS but there is still a need to identify the account owning the order.

| Key       | Value                                                                           |
| --------- | ------------------------------------------------------------------------------- |
| OMSId     | **integer.** The Order Management System on which the order exists. _required_  |
| AccountId | **integer.** The ID of the account under which the order was placed._required._ |
| OrderId   | **long integer.** The order to be canceled._required._                          |

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
{
    "result": true,
    "errormsg": null,
    "errorcode": 0,
    "detail": null
}
```

The response to **CancelOrder** verifies that the call was received, not that the order has been canceled successfully. Individual event updates to the user show order cancellation. To verify that an order has been canceled, call **GetOrderStatus** or **GetOpenOrders.**

| Key       | Value                                                                                                                                                                                                                                                                                                                                                                                                                          |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| result    | **Boolean.** Returns _true_ if the call to cancel the order has been successfully received, otherwise returns _false_.                                                                                                                                                                                                                                                                                                         |
| errormsg  | **string.** A successful receipt of a call to cancel an order returns _null_; the _errormsg_ parameter for an unsuccessful call to cancel an order returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer.** A successfully received call to cancel an order returns 0. An unsuccessfully received call to cancel an order returns one of the _errorcodes_ shown in the _errormsg_ list.                                                                                                                                                                                                                                       |
| detail    | **string.** Message text that the system may send. The contents of this parameter are usually null.                                                                                                                                                                                                                                                                                                                            |
