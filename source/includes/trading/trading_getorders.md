## GetOrders

**Category:** Trading<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

Retrieves a list of the latest states of orders for an account. ReceiveTime in POSIX format X 1000 (milliseconds since 1 January 1970).

Results can also be filtered according to different search parameters such as OrderState, InstrumentId, OrderId etc. This API functions just like [**GetOrdersHistory**](https://23harolds.github.io/slatedoc/?javascript#getordershistory)

A user with Trading permission can retrieve orders only for accounts is associated with; a user with Operator permission can retrieve orders for any account.

<aside class="notice"><strong>Note:</strong> In this call, "Depth" refers to the count of trades to report, not the depth of the order book.</aside>

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("GetOrders", {
  OMSId: 1,
  AccountId: 7,
});

/* Possible payload values
{
"OMSId": 0,
    "AccountId": 0,
    "OrderId": 0,
    "ClientOrderId": 0,
    "OriginalOrderId": 0,
    "OriginalClientOrderId": 0,
    "UserId": 0,
    "OrderState": {
         "Options":  [
            "Unknown",
            "Working",
            "Rejected",
            "Canceled",
            "Expired",
            "FullyExecuted"
        ]
    },
    "OrderType": {
         "Options":  [
            "Unknown",
            "Market",
            "Limit",
            "StopMarket",
            "StopLimit",
            "TrailingStopMarket",
            "TrailingStopLimit",
            "BlockTrade"
        ]
    },
    "InstrumentId": 0,
    "StartTimestamp": 0,
    "EndTimestamp": 0,
    "Depth": 0,
    "Limit": 0,
    "StartIndex": 0,
    "LatestStates": false,
}
*/
```

```http
POST /AP/GetOrders HTTP/1.1
Host: hostname goes here...
aptoken: c5f917b9-f173-4c29-a615-1503d2e78023 //valid sessiontoken
Content-Type: application/json
Content-Length: 41

{
    "OMSId": 1,
    "AccountId": 7
}
```

| Key                   | Value                                                                                                                                                                                                                                                                                                  |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| OMSId                 | **Integer**. The ID of the Order Management System on which the orders took place. If no other values are specified, the call returns the orders associated with the default account for the logged-in user on this Order Management System._required._                                                |
| AccountId             | **Integer**. The account ID that made the trades. A user with Trading permission must be associated with this account, although other users also can be associated with the account._required._                                                                                                        |
| OrderState            | **string.** The current state of the order. Can be used to filter results. If not specified all orders regardless of the order state will be returned. One of:<br />**0** Unknown<br />**1** Working<br />**2** Rejected<br />**3** Canceled<br />**4** Expired<br />**5** Fully Executed._optional._  |
| OrderId               | **long integer**. ID for the order.Can be used to filter results. Can be used to filter for a specific orderid. There is a specific API call [**GetOrderHistoryByOrderId**](https://23harolds.github.io/slatedoc/?javascript#getorderhistorybyorderid) for filtering orders by **OrderId**._optional._ |
| ClientOrderId         | **long integer**. A user-assigned ID for the order (like a purchase-order number assigned by a company).Can be used to filter results. _clientOrderId_ defaults to 0._optional._                                                                                                                       |
| OriginalOrderId       | **long integer**. The original ID of the order. If specified, the call returns changed orders associated with this order ID. Can be used to filter results._optional._                                                                                                                                 |
| OriginalClientOrderId | **long integer**. If the order has been changed, shows the original client order ID, a value that the client can create (much like a purchase order). Can be used to filter results._optional._                                                                                                        |
| UserId                | **integer**. The ID of the user whose account orders will be returned. If not specified, the call returns the orders of the logged-in user.Can be used to filter results._optional._                                                                                                                   |
| InstrumentId          | **long integer**. The ID of the instrument named in the order. If not specified, the call returns orders for all instruments traded by this account. Can be used to filter results._optional._                                                                                                         |
| StartTimestamp        | **long integer**. Date and time at which to begin to fetch the orders in POSIX format. Can be used to filter results._optional._                                                                                                                                                                       |
| EndTimestamp          | **long integer**. Date and time at which to end the orders report, in POSIX format. Can be used to filter results._optional._                                                                                                                                                                          |
| Depth                 | **integer**. In this case, the count of orders to return, counting from the _StartIndex_. If not specified, returns all orders between _BeginTimeStamp_ and _EndTimeStamp_, beginning at _StartIndex_ and working backwards. Can be used to filter results or for pagination._optional._               |
| StartIndex            | **integer**. The starting index into the orders, from 0 (the most recent trade) and moving backwards in time. If not specified, defaults to 0. Can be used to filter results or for pagination._optional._                                                                                             |

### Response

```javascript
[
  {
    Side: "Sell",
    OrderId: 6534,
    Price: 29000.0,
    Quantity: 0.02,
    DisplayQuantity: 0.02,
    Instrument: 1,
    Account: 7,
    AccountName: "harolds",
    OrderType: "Limit",
    ClientOrderId: 0,
    OrderState: "Working",
    ReceiveTime: 1679559217338,
    ReceiveTimeTicks: 638151560173384685,
    LastUpdatedTime: 1679559217344,
    LastUpdatedTimeTicks: 638151560173440317,
    OrigQuantity: 0.02,
    QuantityExecuted: 0.0,
    GrossValueExecuted: 0.0,
    ExecutableValue: 0.0,
    AvgPrice: 0.0,
    CounterPartyId: 0,
    ChangeReason: "NewInputAccepted",
    OrigOrderId: 6534,
    OrigClOrdId: 0,
    EnteredBy: 6,
    UserName: "harold_superuser",
    IsQuote: false,
    InsideAsk: 29000.0,
    InsideAskSize: 0.52,
    InsideBid: 28700.0,
    InsideBidSize: 0.5,
    LastTradePrice: 29000.0,
    RejectReason: "",
    IsLockedIn: false,
    CancelReason: "",
    OrderFlag: "AddedToBook",
    UseMargin: false,
    StopPrice: 0.0,
    PegPriceType: "Bid",
    PegOffset: 0.0,
    PegLimitOffset: 0.0,
    IpAddress: "136.158.50.119",
    IPv6a: 0,
    IPv6b: 0,
    ClientOrderIdUuid: null,
    OMSId: 1,
  },
  {
    Side: "Buy",
    OrderId: 6533,
    Price: 28700.0,
    Quantity: 0.0,
    DisplayQuantity: 0.5,
    Instrument: 1,
    Account: 7,
    AccountName: "harolds",
    OrderType: "Limit",
    ClientOrderId: 0,
    OrderState: "Canceled",
    ReceiveTime: 1679558785657,
    ReceiveTimeTicks: 638151555856568482,
    LastUpdatedTime: 1680019911503,
    LastUpdatedTimeTicks: 638156167115027820,
    OrigQuantity: 0.5,
    QuantityExecuted: 0.0,
    GrossValueExecuted: 0.0,
    ExecutableValue: 0.0,
    AvgPrice: 0.0,
    CounterPartyId: 0,
    ChangeReason: "UserModified",
    OrigOrderId: 6533,
    OrigClOrdId: 0,
    EnteredBy: 6,
    UserName: "harold_superuser",
    IsQuote: false,
    InsideAsk: 29000.0,
    InsideAskSize: 0.5,
    InsideBid: 28700.0,
    InsideBidSize: 0.5,
    LastTradePrice: 29000.0,
    RejectReason: "",
    IsLockedIn: false,
    CancelReason: "UserModified",
    OrderFlag: "AddedToBook, RemovedFromBook",
    UseMargin: false,
    StopPrice: 0.0,
    PegPriceType: "Ask",
    PegOffset: 0.0,
    PegLimitOffset: 0.0,
    IpAddress: "136.158.50.119",
    IPv6a: 0,
    IPv6b: 0,
    ClientOrderIdUuid: null,
    OMSId: 1,
  },
];
```

Returns an array of objects, each object represents an order. The call returns an empty array if there are no orders for the account.

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
