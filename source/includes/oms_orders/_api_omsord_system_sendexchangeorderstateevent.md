## SendExchangeOrderStateEvent

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Changes an order and generates a new *OrderStateEvent.* All information in the Request key-value pairs is required.

An *OrderStateEvent* indicates a change in an order associated with an account. All appropriate subscribers to events will receive the change.

See **SubscribeAccountEvents** for more information about how the AlphaPoint Exchange displays events.

### Request

```json
{
    "exchangeID": 0,
    "omsId": 0,
    "clientOrderId": 0,
    "accountId": 0,
    "productPairId": 0,
    "orderType": 0,
    "side": 0,
    "tIF": 0,
    "pegPriceType": 0,
    "quantity": 0.0,
    "displayQuantity": 0.0,
    "limitPrice": 0.0,
    "stopPrice": 0.0,
    "referencePrice": 0.0,
    "orderExpirationDateTime": 0,
    "orderIdOCO": 0,
    "orderFlag": 0,
    "linkType": 0,
    "exchangeServiceId": "",
    "orderId": 0,
    "enteredBy": 0,
    "counterPartyId": 0,
    "isQuote": true,
    "useMargin": true,
    "bestSellPrice": 0.0,
    "bestSellQuantity": 0.0,
    "bestBuyPrice": 0.0,
    "bestBuyQuantity": 0.0,
    "lastTradePrice": 0.0
}
```
To change the order state, an entire order object must be sent.

| Key                     | Value                                                        |
| ----------------------- | ------------------------------------------------------------ |
| exchangeId              | **integer.** The ID of the Exchange.                         |
| omsId                   | **integer.** The ID of the Order Management System on which the event will be sent. |
| clientOrderId           | **long integer.** A user-assigned ID for the order (like a purchase-order number assigned by a company). The value of *clientOrderId* defaults to 0 if not supplied. |
| accountId               | **integer.** The ID of the account whose order changed.      |
| productPairId           | **integer.** The ID of the product pair making up the trade (product pair = instrument). |
| orderType               | **integer.** A number representing the nature of the order or quote. One of:<br />**0** Unknown<br />**1** Market<br />**2** Limit<br />**3** StopMarket<br />**4** StopLimit<br />**5** TrailingStopMarket<br />**6** TrailingStopLimit<br />**7** BlockTrade |
| side                    | **integer.** A number representing one of the following potential sides of a trade:<br />**0** Buy<br />**1** Sell<br />**2** Short<br />**3** Unknown (an error condition) |
| tIF                     | **integer.** Time-in-Force. An integer that represents the period during which the order or quote is executable. One of:<br />**0** Unknown (an error condition)<br />**1** GTC (good 'til canceled, the default)<br />**2** OPG (execute as close to opening price as possible)<br />**3** IOC (immediate or cancel)<br />**4** FOK (fill or kill immediately)<br />**5** GTX (good 'til executed)<br />**6** GTD (good 'til date) |
| pegPriceType            | **integer.** When entering a *StopTrailing* order, set *pegPriceType* to an integer that corresponds to the type of price that pegs the stop:<br />**1** Last<br />**2** Bid<br />**3** Ask<br />**4** Midpoint |
| quantity                | **real.** The quantity of the order.                         |
| displayQuantity         | **real.** The quantity available to buy or sell that is publicly displayed to the market. To display a *displayQuantity* value, an order must be a Limit order with a reserve. |
| limitPrice              | **real.** The price at which to execute the order, if the order is a Limit order. |
| stopPrice               | **real.** The price at which to execute the order, if the order is a Stop order. |
| referencePrice          | **real.** Used for trailing orders.                          |
| orderExpirationDateTime | **long integer.** The time that the order expires, in POSIX format and UTC time zone. |
| orderIdOCO              | **integer.** The order ID if One Cancels the Other &mdash; if this order is Order A, *orderIdOCO* refers to the order ID of an Order B. If Order B executes, then Order A is canceled. |
| orderFlag               | **integer.** Describes how the order is to be handled. One of:<br />**1** NoAccountRiskCheck<br />**2** AddedToBook<br />**3** RemovedFromBook<br />**8** PostOnly |
| linkType                | **integer.** The value of *LinkType* is used internally. One of:<br />**0** Unknown<br />**1** Cancel<br />**2** Update |
| exchangeServiceId       | **string.** The name of the matching engine that executes this order. |
| orderId                 | **integer.** The ID of the order that generated the changed state event. |
| enteredBy               | **integer.** The ID of the user who entered the order that generated the changed state event. |
| counterPartyId          | **integer.** The ID of the other party in the trade that generated the changed state event. |
| isQuote                 | **Boolean.** The value is *true* if this order is a quote; *false* if it is not a quote. |
| useMargin               | **Boolean.** The value is *true* if this order uses margin; *false* if it does not. |
| bestSellPrice           | **real.** The best selling price for the instrument at the time of the change event. |
| bestSellQuantity        | **real.** The quantity of the instrument available at the best selling price at the time of the change event. |
| bestBuyPrice            | **real.** The best buying price for the instrument at the time of the change event. |
| bestBuyQuantity         | **real.** The quantity of the instrument available at the best buying price at the time of the change event. |
| lastTradePrice          | **real.** The last price at which the instrument was successfully traded prior to the change event. |







### Response

```json
{
    "result": true,
    "errormsg": "",
    "errorcode": 0,
    "detail": ""
}
```
The Response is a standard response object.

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean.** If the call has been successfully received by the Order Management System, *result* is *true;* otherwise it is *false.* |
| errormsg  | **string.** A successful receipt of the call returns *null.* The *errormsg* key for an unsuccessful call returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer.** A successful receipt of the call returns 0. An unsuccessful receipt of the call returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send.           |
