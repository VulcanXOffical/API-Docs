## SendOrder

**Category:** Trading<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Asynchronous

Creates an order.

Anyone submitting an order should also subscribe to the various market data and event feeds, or call **GeOpenOrders** or **GetOrderStatus** to monitor the status of the order. If the order is not in a state to be executed, **GetOpenOrders** will not return it.

A user with Trading permission can create an order only for those accounts and instruments with which the user is associated; a user with Operator permissions can create an order for any account and instrument.

<aside class="notice"><strong>Note:</strong> Call Type is asynchronous.</aside>

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

//Limit order
await apex.RPCPromise("SendOrder", {
  InstrumentId: 9,
  OMSId: 1,
  AccountId: 9,
  TimeInForce: 1,
  ClientOrderId: 0,
  OrderIdOCO: 0,
  UseDisplayQuantity: false,
  Side: 0,
  Quantity: 1,
  OrderType: 2,
  PegPriceType: 3,
  LimitPrice: 31000,
});
//Market order
await apex.RPCPromise("SendOrder", {
  InstrumentId: 9,
  OMSId: 1,
  AccountId: 9,
  TimeInForce: 1,
  ClientOrderId: 0,
  OrderIdOCO: 0,
  UseDisplayQuantity: false,
  Side: 0,
  OrderType: 1,
  PegPriceType: 3,
  Quantity: 0.5,
});
//Order by value: In a marker order, a user can opt to input how much he/she is willing sell or buy, no need to input quantity
await apex.RPCPromise("SendOrder", {
  InstrumentId: 9,
  OMSId: 1,
  AccountId: 9,
  TimeInForce: 1,
  ClientOrderId: 0,
  OrderIdOCO: 0,
  UseDisplayQuantity: false,
  Side: 0,
  OrderType: 1,
  PegPriceType: 3,
  Value: 10,
});
```

```http
POST /AP/SendOrder HTTP/1.1
Host: hostname goes here...
aptoken: 604f9459-163f-4114-8ecc-928597554747
Content-Type: application/json
Content-Length: 252

//Limit order
await apex.RPCPromise("SendOrder", {
  InstrumentId: 9,
  OMSId: 1,
  AccountId: 9,
  TimeInForce: 1,
  ClientOrderId: 0,
  OrderIdOCO: 0,
  UseDisplayQuantity: false,
  Side: 0,
  Quantity: 1,
  OrderType: 2,
  PegPriceType: 3,
  LimitPrice: 31000,
});
//Market order
await apex.RPCPromise("SendOrder", {
  InstrumentId: 9,
  OMSId: 1,
  AccountId: 9,
  TimeInForce: 1,
  ClientOrderId: 0,
  OrderIdOCO: 0,
  UseDisplayQuantity: false,
  Side: 0,
  OrderType: 1,
  PegPriceType: 3,
  Quantity: 0.5,
});
//Order by value: In a marker order, a user can opt to input how much he/she is willing sell or buy, no need to input quantity
await apex.RPCPromise("SendOrder", {
  InstrumentId: 9,
  OMSId: 1,
  AccountId: 9,
  TimeInForce: 1,
  ClientOrderId: 0,
  OrderIdOCO: 0,
  UseDisplayQuantity: false,
  Side: 0,
  OrderType: 1,
  PegPriceType: 3,
  Value: 10,
});
```

If OrderType=1 (Market), Side=0 (Buy), and LimitPrice is supplied, the Market order will execute up to the value specified

| Key                | Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| InstrumentId       | **integer.** The ID of the instrument being traded.                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| OMSId              | **integer.** The ID of the Order Management System where the instrument is being traded.                                                                                                                                                                                                                                                                                                                                                                                                                          |
| AccountId          | **integer.** The ID of the account placing the order.                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| TimeInForce        | **integer.** An integer that represents the period during which the new order is executable. One of:<br />**0** Unknown (error condition)<br />**1** GTC (good 'til canceled, the default)<br />**2** OPG (execute as close to opening price as possible)<br />**3** IOC (immediate or canceled)<br />**4** FOK (fill-or-kill &mdash; fill immediately or kill immediately)<br />**5** GTX (good 'til executed)<br />**6** GTD (good 'til date)                                                                   |
| ClientOrderId      | **long integer.** A user-assigned ID for the order (like a purchase-order number assigned by a company). This ID is useful for recognizing future states related to this order. _ClientOrderId_ defaults to 0. Starting APEX version 4.2, duplicate client orderid of two open orders of the same account is not allowed, the incoming order with the same clientorderid will get rejected.                                                                                                                       |
| OrderIdOCO         | **long integer.** The order ID if One Cancels the Other — If this order is order A, _OrderIdOCO_ refers to the order ID of an order B (which is _not_ the order being created by this call). If order B executes, then order A created by this call is canceled. You can also set up order B to watch order A in the same way, but that may require an update to order B to make it watch this one, which could have implications for priority in the order book. See **CancelReplaceOrder** and **ModifyOrder.** |
| UseDisplayQuantity | **Boolean.** If you enter a Limit order with a reserve(reserve order), you must set _UseDisplayQuantity_ to _true_.                                                                                                                                                                                                                                                                                                                                                                                               |
| Side               | **integer.** A number representing on of the following potential sides of a trade. One of:<br />**0** Buy<br />**1** Sell<br />**2** Short<br />**3** unknown (an error condition)                                                                                                                                                                                                                                                                                                                                |
| Quantity           | **real.** The quantity of the instrument being ordered.                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| OrderType          | **integer.** A number representing the nature of the order. One of:<br />**0** Unknown<br />**1** Market<br />**2** Limit<br />**3** StopMarket<br />**4** StopLimit<br />**5** TrailingStopMarket<br />**6** TrailingStopLimit<br />**7** BlockTrade.                                                                                                                                                                                                                                                            |
| PegPriceType       | **integer.** When entering a stop/trailing order, set _PegPriceType_ to an integer that corresponds to the type of price that pegs the stop:<br />**1** Last<br />**2** Bid<br />**3** Ask<br />**4** Midpoint                                                                                                                                                                                                                                                                                                    |
| LimitPrice         | **real.** The price at which to execute the order, if the order is a Limit order.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| DisplayQuantity    | **integer** If _UseDisplayQuantity_ is set to **_true_**, you must set a value of this field greater than 0, else, order will not appear in the orderbook.                                                                                                                                                                                                                                                                                                                                                        |

### Response

```javascript
{
    "status": "Accepted",
    "errormsg": "",
    "OrderId": 6500
}
//Possible error messages
//Order is rejected due to lack of funds
{
    "status": "Rejected",
    "errormsg": "Not_Enough_Funds",
    "errorcode": 101
}
//Order is rejected due to duplicate Client_OrderId, it means that the order you are sending has the same Client_OrderId with your other working/open order.
{
    "status": "Rejected",
    "errormsg": "Invalid_ClientOrderId",
    "errorcode": 101
}
```

```http
{
    "status": "Accepted",
    "errormsg": "",
    "OrderId": 6500
}
//Possible error messages
//Order is rejected due to lack of funds
{
    "status": "Rejected",
    "errormsg": "Not_Enough_Funds",
    "errorcode": 101
}
//Order is rejected due to duplicate Client_OrderId, it means that the order you are sending has the same Client_OrderId with your other working/open order.
{
    "status": "Rejected",
    "errormsg": "Invalid_ClientOrderId",
    "errorcode": 101
}
```

| Key      | Value                                                                                                                                |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| status   | **string**. If the order is accepted by the system, it returns "Accepted," if not it returns "Rejected."<br />Accepted<br />Rejected |
| errormsg | **string**. Any error message the server returns.                                                                                    |
| OrderId  | **long integer**. The ID assigned to the order by the server. This allows you to track the order.                                    |
