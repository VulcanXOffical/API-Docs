## ModifyOrder

**Category:** User<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

Reduces an order’s quantity without losing priority in the order book. An order’s quantity can only be reduced. The other call that can modify an order &mdash; **CancelReplaceOrder** &mdash; resets order book priority, but you can use it to increase an order quantity and also change the limitprice.

<aside class="notice"><strong>Note:</strong> <strong>ModifyOrder</strong> does not surrender or reset order book priority.</aside>

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");
await apex.RPCPromise("ModifyOrder", {
  OMSId: 1,
  OrderId: 6507,
  InstrumentId: 9,
  Quantity: 0.1,
  AccountId: 9,
});
```

```http
POST /AP/ModifyOrder HTTP/1.1
Host: hostname goes here...
aptoken: 356cdf76-b767-4af5-890e-837ea17030d0
Content-Type: application/json
Content-Length: 109

{
    "OMSId": 1,
    "OrderId": 6507,
    "InstrumentId": 9,
    "Quantity": 0.1,
    "AccountId": 9
}
```

| Key          | Value                                                                                                                          |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| OMSId        | **integer.** The ID of the Order Management System where the original order was placed._required._                             |
| OrderId      | **long integer.** The ID of the order to be modified. The ID was supplied by the server when the order was created._required._ |
| InstrumentId | **integer.** The ID of the instrument traded in the order._required._                                                          |
| Quantity     | **real.** The new quantity of the order. This value can only be reduced from a previous quantity._required._                   |
| AccountId    | **integer.** Account for which order will be modified._required._                                                              |

### Response

```javascript
{
    "result": true,
    "errormsg": null,
    "errorcode": 0,
    "detail": null
}

//Possible error/s
//Quantity defined is greater than the existing quantity of the order being modified. This API can only reduce the quantity of the existing order.
{
    "result": false,
    "errormsg": "Invalid Quantity",
    "errorcode": 100,
    "detail": null
}

//One or more required fields are not defined
{
    "result": false,
    "errormsg": "Invalid Request",
    "errorcode": 100,
    "detail": "Not all required fields are provided"
}
```

```http
{
    "result": true,
    "errormsg": null,
    "errorcode": 0,
    "detail": null
}

//Possible error/s
//Quantity defined is greater than the existing quantity of the order being modified. This API can only reduce the quantity of the existing order.
{
    "result": false,
    "errormsg": "Invalid Quantity",
    "errorcode": 100,
    "detail": null
}

//One or more required fields are not defined
{
    "result": false,
    "errormsg": "Invalid Request",
    "errorcode": 100,
    "detail": "Not all required fields are provided"
}
```

The response acknowledges the successful receipt of your request to modify an order; it does not indicate that the order has been modified. To find if an order has been modified, check using **GetOpenOrders** and **GetOrderHistory.**

| Key       | Value                                                                                                                                                                                                                                                                                                                                                    |
| --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result    | **Boolean.** The successful receipt of a modify order request returns _true_; otherwise, returns _false_. This is the acknowledgment of receipt of the request to modify, not a confirmation that the modification has taken place.                                                                                                                      |
| errormsg  | **string.** A successful receipt of a modify request returns _null_; the _errormsg_ parameter for an unsuccessful request returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104) |
| errorcode | **integer.** The receipt of a successful request to modify returns 0. An unsuccessful request returns one of the _errorcodes_ shown in the _errormsg_ list.                                                                                                                                                                                              |
| detail    | **string.** Message text that the system may send. Usually _null_.                                                                                                                                                                                                                                                                                       |
