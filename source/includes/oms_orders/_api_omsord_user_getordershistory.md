## GetOrdersHistory

**Category:** User<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

Retrieves an array of multiple orders (hence, **GetOrdersHistory** with plural *Orders*) for the specified account, order ID, user, instrument, or time stamp. The history starts at index *i*, where *i* is an integer identifying a specific order (the most recent order has an index of 0). “Depth” is the count of trades to report backwards from *startIndex*. All values in the call other than *OMSId* are optional.

For example, if *depth* = 200 and *startIndex* = 0, the history returns 200 orders into the past starting with the most recent (0) order. If *depth* = 200 and *startIndex* = 100, the history returns 200 orders into the past starting at 100 orders in the past.

The owner of the trading venue determines how long to retain order history before archiving.

A user with Trading permission can retrieve a history only for accounts with which the user is associated; a user with Operator permission can retrieve a history for any user or account.

<aside class="notice"><strong>Note:</strong> In this call, "Depth" refers to the count of trades to report, not the depth of the order book.</aside>

### Request

```json
{
    "omsId": 0,
    "accountId": 0,
    "clientOrderId": 0,
    "originalOrderId": 0,
    "originalClientOrderId": 0,
    "userId": 0,
    "instrumentId": 0,
    "startTimestamp": 0,
    "endTimestamp": 0,
    "depth": 100,
    "startIndex": 0
}
```

All values other than *OMSId* are optional. If account ID is not supplied, the Exchange assumes the default account of the user issuing the call.

| Key                   | Value                                                        |
| --------------------- | ------------------------------------------------------------ |
| omsId                 | **Integer**. The ID of the Order Management System on which the orders took place. *Required*. If no other values are specified, the call returns the orders associated with the default account for the logged-in user on this Order Management System. |
| accountId             | **Integer**. The account ID that made the trades. A user with Trading permission must be associated with this account, although other users also can be associated with the account. If no account ID is supplied, the system assumes the default account for the logged-in user. |
| ClientOrderId         | **long integer**. A user-assigned ID for the order (like a purchase-order number assigned by a company). *clientOrderId* defaults to 0. |
| originalOrderId       | **long integer**. The original ID of the order. If specified, the call returns changed orders associated with this order ID. |
| originalClientOrderId | **long integer**. If the order has been changed, shows the original client order ID, a value that the client can create (much like a purchase order). |
| userId                | **integer**. The ID of the user whose account orders will be returned. If not specified, the call returns the orders of the logged-in user. |
| instrumentId          | **long integer**. The ID of the instrument named in the order. If not specified, the call returns orders for all instruments traded by this account. |
| startTimestamp        | **long integer**. Date and time at which to begin the orders history, in POSIX format. |
| endTimestamp          | **long integer**. Date and time at which to end the orders report, in POSIX format. |
| depth                 | **integer**. In this case, the count of orders to return, counting from the *StartIndex*. If not specified, returns all orders between *BeginTimeStamp* and *EndTimeStamp*, beginning at *StartIndex* and working backwards. |
| startIndex            | **integer**. The starting index into the order history, from 0 (the most recent trade) and moving backwards in time. If not specified, defaults to 0. |

### Response

```json
[
    {
        "Side": "Buy",
        "OrderId": 0,
        "Price":  0.0,
        "Quantity":  0.0,
        "DisplayQuantity":  0.0,
        "Instrument": 0,
        "Account": 0,
        "OrderType": "Unknown",
        "ClientOrderId": 0,
        "OrderState": "Unknown",
        "ReceiveTime": 0,
        "ReceiveTimeTicks": 0,
        "OrigQuantity": 0.0,
        "QuantityExecuted": 0.0,
        "AvgPrice": 0.0,
        "CounterPartyId": 0,
        "ChangeReason": "Unknown",
        "OrigOrderId": 0,
        "OrigClOrdId": 0,
        "EnteredBy": 0,
        "IsQuote": false,
        "InsideAsk": 0.0,
        "InsideAskSize": 0.0,
        "InsideBid": 0.0,
        "InsideBidSize": 0.0,
        "LastTradePrice": 0.0,
        "RejectReason": "",
        "IsLockedIn": false,
        "CancelReason": "",
        "OMSId": 0
    },
]
```

The call **GetOrdersHistory** returns an array containing all four types of orders for the named account. The call returns an empty array if there are no orders for the account.

| Key                               | Value                                                        |
| --------------------------------- | ------------------------------------------------------------ |
| Side                              | **string.** The side of a trade. One of:<br />**0** Buy<br />**1**  Sell<br />**2** Short<br />**3** Unknown (an error condition)   |
| OrderId                           | **long integer.** The ID of the open order. The *OrderID* is unique in each Order Management System. |
| Price                             | **real.** The price at which the buy or sell has been ordered. |
| Quantity                          | **real.** The quantity of the product to be bought or sold.  |
| DisplayQuantity                   | **real.** The quantity available to buy or sell that is publicly displayed to the market. To display a *displayQuantity* value, an order must be a Limit order with a reserve. |
| Instrument                        | **integer.** ID of the instrument being traded. The call  **GetInstruments** can supply the instrument IDs that are available. |
| orderType                         | **string.** Describes the type of order this is. One of:<br />**0** Unknown (an error condition)<br />**1** Market order<br />**2** Limit<br />**3** StopMarket<br />**4** StopLimit<br />**5** TrailingStopMarket<br />**6** TrailingStopLimit<br />**7** BlockTrade |
| ClientOrderId                     | **long integer.** An ID supplied by the client to identify the order (like a purchase order number). The *ClientOrderId* defaults to 0 if not supplied.                       |
| OrderState                        | **string.** The current state of the order. One of:<br />**0** Unknown<br />**1** Working<br />**2** Rejected<br />**3** Canceled<br />**4** Expired<br />**5** Fully Executed.                           |
| ReceiveTime                       | **long integer.** Time stamp of the order in POSIX format x 1000 (milliseconds since 1/1/1970 in UTC time zone).   |
| ReceiveTimeTicks                  | **long integer.** Time stamp of the order Microsoft Ticks format and UTC time zone. **Note:** Microsoft Ticks format is usually provided as a string. Here it is provided as a long integer.   |
| OrigQuantity                      | **real.** If the open order has been changed or partially filled, this value shows the original quantity of the order.  |
| QuantityExecuted                  | **real.** If the open order has been at least partially executed, this value shows the amount that has been executed.  |
| AvgPrice                          | **real.** The average executed price for the instrument in the order.   |
| CounterPartyId                    | **integer.** The ID of the other party in an off-market trade.  |
| ChangeReason                      | **string.** If the order has been changed, this string value holds the reason. One of:<br />**0** Unknown<br />**1** NewInputAccepted<br />**2** NewInputRejected<br />**3** OtherRejected<br />**4** Expired<br />**5** Trade<br />**6** SystemCanceled_NoMoreMarket<br />**7** SystemCanceled_BelowMinimum<br />**8** SystemCanceled_PriceCollar<br />**9** SystemCanceled_MarginFailed<br />**100** UserModified  |
| OrigOrderId                       | **integer.** If the order has been changed, this is the ID of the original order.  |
| OrigClOrdId                       | **integer.** If the order has been changed, this is the ID of the original client order ID.  |
| EnteredBy                         | **integer.** The user ID of the person who entered the order.  |
| IsQuote                           | **Boolean.** If this order is a quote, the value for *IsQuote* is *true,* else *false.*  |
| InsideAsk                         | **real.** If this order is a quote, this value is the Inside Ask price.  |
| InsideAskSize                     | **real.** If this order is a quote, this value is the quantity of the Inside Ask quote.  |
| InsideBid                         | **real.** If this order is a quote, this value is the Inside Bid price.   |
| InsideBidSize                     | **real.** If this order is a quote, this value is the quantity of the Inside Bid quote.  |
| LastTradePrice                    | **real.** The last price that this instrument traded at.  |
| RejectReason                      | **string.** If this open order has been rejected, this string holds the reason for the rejection.  |
| IsLockedIn                        | **Boolean.** For a block trade, if both parties to the block trade agree that one of the parties will report the trade for both sides, this value is *true.* Othersise, *false.*  |
| CancelReason                      | **string.** If this order has been canceled, this string holds the cancelation reason.  |
| OMSId                             | **integer.** The ID of the Order Management System on which the order took place.  |

