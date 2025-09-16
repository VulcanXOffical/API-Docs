## SendOrderList

**Category:** Trading<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Asynchronous

Sends or creates a list of orders. Payload is an array containing JSON object/s, each JSON object represents a single order. The orders can be assorted, means that it can be for different instruments and different accounts.

Anyone submitting an order should also subscribe to the various market data and event feeds, or call **GeOpenOrders** or **GetOrderStatus** to monitor the status of the order. If the order is not in a state to be executed, **GetOpenOrders** will not return it.

A user with Trading permission can create an order only for those accounts and instruments with which the user is associated; a user with Operator permissions can create an order for any account and instrument.

<aside class="notice"><strong>Note:</strong> Call Type is asynchronous.</aside>

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("SendOrderList", [
  {
    InstrumentId: 2,
    OMSId: 1,
    AccountId: 185,
    TimeInForce: 1,
    ClientOrderId: 0,
    OrderIdOCO: 0,
    UseDisplayQuantity: false,
    Side: 0,
    Quantity: 0.02,
    OrderType: 2,
    PegPriceType: "3",
    LimitPrice: 23436,
  },
  {
    InstrumentId: 2,
    OMSId: 1,
    AccountId: 185,
    TimeInForce: 1,
    ClientOrderId: 0,
    OrderIdOCO: 0,
    UseDisplayQuantity: false,
    Side: 0,
    Quantity: 0.02,
    OrderType: 2,
    PegPriceType: "3",
    LimitPrice: 23436,
  },
]);
```

```http
POST /AP/SendOrderList HTTP/1.1
Host: hostname goes here...
aptoken: f7e2c811-a9db-454e-9c9e-77533baf92d9 //valid sessiontoken
Content-Type: application/json
Content-Length: 583

[
  {
    "InstrumentId": 2,
    "OMSId": 1,
    "AccountId": 185,
    "TimeInForce": 1,
    "ClientOrderId": 0,
    "OrderIdOCO": 0,
    "UseDisplayQuantity": false,
    "Side": 0,
    "Quantity": 0.02,
    "OrderType": 2,
    "PegPriceType": "3",
    "LimitPrice": 23436
  },
  {
    "InstrumentId": 2,
    "OMSId": 1,
    "AccountId": 185,
    "TimeInForce": 1,
    "ClientOrderId": 0,
    "OrderIdOCO": 0,
    "UseDisplayQuantity": false,
    "Side": 0,
    "Quantity": 0.02,
    "OrderType": 2,
    "PegPriceType": "3",
    "LimitPrice": 23436
  }
]
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
    "result": false, //It returns false but the request wenth through successfully
    "errormsg": "Operation In Process",
    "errorcode": 107,
    "detail": null
}
```

```http
{
    "result": false,
    "errormsg": "Operation In Process",
    "errorcode": 107,
    "detail": null
}
```

| Key       | Value                                                                                                                                                                                                                                                                                                         |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result    | **Boolean**. A successful request returns true; and unsuccessful request (an error condition) returns false.                                                                                                                                                                                                  |
| errormsg  | **string**. A successful request returns null; the _errormsg_ parameter for an unsuccessful request returns one of the following messages: Not Authorized (errorcode 20), Invalid Request (errorcode 100), Operation Failed (errorcode 101), Server Error (errorcode 102), Resource Not Found (errorcode 104) |
| errorcode | **integer**. A successful request returns 0. An unsuccessful request returns one of the _errorcodes_ shown in the _errormsg_ list.                                                                                                                                                                            |
| detail    | **string**. Message text that the system may send. Usually _null_.                                                                                                                                                                                                                                            |
