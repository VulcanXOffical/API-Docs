## GetOrderStatus

**Category:** Trading<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

Retrieves the status information for a single order.

A user with Trading permission can retrieve status information for accounts and orders with which the user is associated; a user with Operator permission can retreive status information for any account or order ID.

### Request

```javascript
const { APEX } = require("VulcanX-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("GetOrderStatus", {
  OMSId: 1,
  AccountId: 7,
  OrderId: 6562,
});
```

```http
POST /AP/GetOrderStatus HTTP/1.1
Host: hostname goes here...
aptoken: f7e2c811-a9db-454e-9c9e-77533baf92d9 //valid session token
Content-Type: application/json
Content-Length: 63

{
    "OMSId": 1,
    "AccountId": 7,
    "OrderId": 6562
}
```

| Key       | Value                                                                                                                                                           |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| OMSId     | **Integer.** The ID of the Order Management System on which the order was placed._optional._                                                                    |
| AccountId | **integer.** The ID of the account under which the order was placed._required._                                                                                 |
| OrderId   | **integer.** The ID of the order whose status will be returned.If not provided, the most recent order of the account will be returned._conditionally optional._ |

### Response

```javascript
{
  "Side": "Buy",
  "OrderId": 6562,
  "Price": 23436.0,
  "Quantity": 0.02,
  "DisplayQuantity": 0.0,
  "Instrument": 1,
  "Account": 7,
  "AccountName": "harolds",
  "OrderType": "Limit",
  "ClientOrderId": 0,
  "OrderState": "Working",
  "ReceiveTime": 1680020672485,
  "ReceiveTimeTicks": 638156174724846502,
  "LastUpdatedTime": 1680020672485,
  "LastUpdatedTimeTicks": 638156174724852936,
  "OrigQuantity": 0.02,
  "QuantityExecuted": 0.0,
  "GrossValueExecuted": 0.0,
  "ExecutableValue": 0.0,
  "AvgPrice": 0.0,
  "CounterPartyId": 0,
  "ChangeReason": "NewInputAccepted",
  "OrigOrderId": 6562,
  "OrigClOrdId": 0,
  "EnteredBy": 0,
  "UserName": "",
  "IsQuote": false,
  "InsideAsk": 29000.0,
  "InsideAskSize": 0.52,
  "InsideBid": 23436.0,
  "InsideBidSize": 0.0,
  "LastTradePrice": 29000.0,
  "RejectReason": "",
  "IsLockedIn": false,
  "CancelReason": "",
  "OrderFlag": "AddedToBook",
  "UseMargin": false,
  "StopPrice": 0.0,
  "PegPriceType": "Ask",
  "PegOffset": 0.0,
  "PegLimitOffset": 0.0,
  "IpAddress": null,
  "IPv6a": 0,
  "IPv6b": 0,
  "ClientOrderIdUuid": null,
  "OMSId": 1
}
```

```http
{
    "Side": "Buy",
    "OrderId": 6562,
    "Price": 23436.000000000000000000000000,
    "Quantity": 0.0200000000000000000000000000,
    "DisplayQuantity": 0.0000000000000000000000000000,
    "Instrument": 1,
    "Account": 7,
    "AccountName": "harolds",
    "OrderType": "Limit",
    "ClientOrderId": 0,
    "OrderState": "Working",
    "ReceiveTime": 1680020672485,
    "ReceiveTimeTicks": 638156174724846502,
    "LastUpdatedTime": 1680020672485,
    "LastUpdatedTimeTicks": 638156174724852936,
    "OrigQuantity": 0.0200000000000000000000000000,
    "QuantityExecuted": 0.0000000000000000000000000000,
    "GrossValueExecuted": 0.0000000000000000000000000000,
    "ExecutableValue": 0.0000000000000000000000000000,
    "AvgPrice": 0.0000000000000000000000000000,
    "CounterPartyId": 0,
    "ChangeReason": "NewInputAccepted",
    "OrigOrderId": 6562,
    "OrigClOrdId": 0,
    "EnteredBy": 0,
    "UserName": "",
    "IsQuote": false,
    "InsideAsk": 29000.000000000000000000000000,
    "InsideAskSize": 0.5200000000000000000000000000,
    "InsideBid": 23436.000000000000000000000000,
    "InsideBidSize": 0.0000000000000000000000000000,
    "LastTradePrice": 29000.000000000000000000000000,
    "RejectReason": "",
    "IsLockedIn": false,
    "CancelReason": "",
    "OrderFlag": "AddedToBook",
    "UseMargin": false,
    "StopPrice": 0.0000000000000000000000000000,
    "PegPriceType": "Ask",
    "PegOffset": 0.0000000000000000000000000000,
    "PegLimitOffset": 0.0000000000000000000000000000,
    "IpAddress": null,
    "IPv6a": 0,
    "IPv6b": 0,
    "ClientOrderIdUuid": null,
    "OMSId": 1
}
```

The call **GetOrderStatus** returns a JSON object which contains the data of a specific order.

| Key              | Value                                                                                                                                                                                                                                                                                                                                                                                                               |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Side             | **string.** The side of a trade. One of:<br />**0** Buy<br />**1** Sell<br />**2** Short<br />**3** Unknown (an error condition)                                                                                                                                                                                                                                                                                    |
| OrderId          | **long integer.** The ID of the open order. The _OrderID_ is unique in each Order Management System.                                                                                                                                                                                                                                                                                                                |
| Price            | **real.** The price at which the buy or sell has been ordered.                                                                                                                                                                                                                                                                                                                                                      |
| Quantity         | **real.** The quantity of the product to be bought or sold.                                                                                                                                                                                                                                                                                                                                                         |
| DisplayQuantity  | **real.** The quantity available to buy or sell that is publicly displayed to the market. To display a _displayQuantity_ value, an order must be a Limit order with a reserve.                                                                                                                                                                                                                                      |
| Instrument       | **integer.** ID of the instrument being traded. The call **GetInstruments** can supply the instrument IDs that are available.                                                                                                                                                                                                                                                                                       |
| orderType        | **string.** Describes the type of order this is. One of:<br />**0** Unknown (an error condition)<br />**1** Market order<br />**2** Limit<br />**3** StopMarket<br />**4** StopLimit<br />**5** TrailingStopMarket<br />**6** TrailingStopLimit<br />**7** BlockTrade                                                                                                                                               |
| ClientOrderId    | **long integer.** An ID supplied by the client to identify the order (like a purchase order number). The _ClientOrderId_ defaults to 0 if not supplied.                                                                                                                                                                                                                                                             |
| OrderState       | **string.** The current state of the order. One of:<br />**0** Unknown<br />**1** Working<br />**2** Rejected<br />**3** Canceled<br />**4** Expired<br />**5** Fully Executed.                                                                                                                                                                                                                                     |
| ReceiveTime      | **long integer.** Time stamp of the order in POSIX format x 1000 (milliseconds since 1/1/1970 in UTC time zone).                                                                                                                                                                                                                                                                                                    |
| ReceiveTimeTicks | **long integer.** Time stamp of the order Microsoft Ticks format and UTC time zone. **Note:** Microsoft Ticks format is usually provided as a string. Here it is provided as a long integer.                                                                                                                                                                                                                        |
| OrigQuantity     | **real.** If the open order has been changed or partially filled, this value shows the original quantity of the order.                                                                                                                                                                                                                                                                                              |
| QuantityExecuted | **real.** If the open order has been at least partially executed, this value shows the amount that has been executed.                                                                                                                                                                                                                                                                                               |
| AvgPrice         | **real.** The average executed price for the instrument in the order.                                                                                                                                                                                                                                                                                                                                               |
| CounterPartyId   | **integer.** The ID of the other party in an off-market trade.                                                                                                                                                                                                                                                                                                                                                      |
| ChangeReason     | **string.** If the order has been changed, this string value holds the reason. One of:<br />**0** Unknown<br />**1** NewInputAccepted<br />**2** NewInputRejected<br />**3** OtherRejected<br />**4** Expired<br />**5** Trade<br />**6** SystemCanceled_NoMoreMarket<br />**7** SystemCanceled_BelowMinimum<br />**8** SystemCanceled_PriceCollar<br />**9** SystemCanceled_MarginFailed<br />**100** UserModified |
| OrigOrderId      | **integer.** If the order has been changed, this is the ID of the original order.                                                                                                                                                                                                                                                                                                                                   |
| OrigClOrdId      | **integer.** If the order has been changed, this is the ID of the original client order ID.                                                                                                                                                                                                                                                                                                                         |
| EnteredBy        | **integer.** The user ID of the person who entered the order.                                                                                                                                                                                                                                                                                                                                                       |
| IsQuote          | **Boolean.** If this order is a quote, the value for _IsQuote_ is _true,_ else _false._                                                                                                                                                                                                                                                                                                                             |
| InsideAsk        | **real.** If this order is a quote, this value is the Inside Ask price.                                                                                                                                                                                                                                                                                                                                             |
| InsideAskSize    | **real.** If this order is a quote, this value is the quantity of the Inside Ask quote.                                                                                                                                                                                                                                                                                                                             |
| InsideBid        | **real.** If this order is a quote, this value is the Inside Bid price.                                                                                                                                                                                                                                                                                                                                             |
| InsideBidSize    | **real.** If this order is a quote, this value is the quantity of the Inside Bid quote.                                                                                                                                                                                                                                                                                                                             |
| LastTradePrice   | **real.** The last price that this instrument traded at.                                                                                                                                                                                                                                                                                                                                                            |
| RejectReason     | **string.** If this open order has been rejected, this string holds the reason for the rejection.                                                                                                                                                                                                                                                                                                                   |
| IsLockedIn       | **Boolean.** For a block trade, if both parties to the block trade agree that one of the parties will report the trade for both sides, this value is _true._ Othersise, _false._                                                                                                                                                                                                                                    |
| CancelReason     | **string.** If this order has been canceled, this string holds the cancelation reason.                                                                                                                                                                                                                                                                                                                              |
| OMSId            | **integer.** The ID of the Order Management System on which the order took place.                                                                                                                                                                                                                                                                                                                                   |
