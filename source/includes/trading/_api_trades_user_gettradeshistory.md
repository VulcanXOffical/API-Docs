## GetTradesHistory

**Category:** Trading<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

Retrieves a list of trades for a specified account, order ID, user, instrument, or starting and ending time stamp. The returned list begins at start index _i,_ where _i_ is an integer identifying a specific trade in reverse order; that is, the most recent trade has an index of 0. “Depth” is the count of trades to report backwards from _StartIndex_.

Users with Trading permission can retrieve trade history for accounts with which they are associated; users with Operator permission can retrieve trade history for any account.

<aside class="warning"><strong>Caution</strong>: You must coordinate *StartIndex*, *Depth*, *StartTimeStamp*, and *EndTimeStamp* to retrieve the historical information you need. As the diagram shows, it is possible to specify values (for example, *EndTimeStamp* and *Depth*) that can exclude information you may want (the red areas).</aside>

<aside class="notice"><strong>Note</strong>: In this call, “Depth” refers not to the depth of the order book, but to the count of trades to report. The owner of the trading venue determines how long to retain order history before archiving.</aside>

### Request

> All values in the request other than omsId are optional.

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");
await apex.RPCPromise("GetTradesHistory", {
  OMSId: 1,
  AccountId: 0,
  InstrumentId: 0,
  TradeId: 0,
  OrderId: 0,
  UserId: 0,
  StartTimestamp: 0,
  EndTimestamp: 0,
  Depth: 2,
  StartIndex: 0,
  ExecutionId: 0,
});
```

```http
POST /ap/GetTradesHistory HTTP/1.1
Host: hostname goes here...
Content-Type: application/json
aptoken: d7676b7e-0290-1ad2-c08a-1280888ffda7
Content-Length: 211

{
  "OMSId": 1,
  "AccountId": 0,
  "InstrumentId": 0,
  "TradeId": 0,
  "OrderId": 0,
  "UserId": 0,
  "StartTimestamp": 0,
  "EndTimestamp": 0,
  "Depth": 2,
  "StartIndex": 0,
  "ExecutionId": 0
}
```

| Key            | Value                                                                                                                                                                                                                        |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| omsId          | **Integer.** The ID of the Order Management System on which the trades took place._required._                                                                                                                                |
| accountId      | **Integer.** The account ID that made the trades. If no account ID is supplied, the system assumes the default account for the logged-in user making the call._optional_                                                     |
| instrumentId   | **long integer.** The ID of the instrument whose trade history is reported. If no instrument ID is included, the system returns trades for all instruments associated with the account ID and OMS._optional._                |
| tradeId        | **integer.** The ID of a specific trade. If you specify _TradeId_, **GetTradesHistory** can return all states for a single trade._optional._                                                                                 |
| orderId        | **integer.** The ID of the order resulting in the trade. If specified, the call returns all trades associated with the order._optional._                                                                                     |
| userId         | **integer.** The ID of the logged-in user. If not specified, the call returns trades associated with the users belonging to the default account for the logged-in user of this OMS._optional._                               |
| startTimeStamp | **long integer.** The historical date and time at which to begin the trade report, in POSIX format. If not specified, reverts to the start date of this account on the trading venue._optional._                             |
| endTimeStamp   | **long integer.** Date at which to end the trade report, in POSIX format._optional._                                                                                                                                         |
| depth          | **integer.** In this case, the count of trades to return, counting from the _StartIndex_. If _Depth_ is not specified, returns all trades between _BeginTimeStamp_ and _EndTimeStamp_, beginning at _StartIndex_._optional._ |
| startIndex     | **integer.** The starting index into the history of trades, from 0 (the most recent trade) and moving backwards in time. If not specified, defaults to 0._optional._                                                         |
| executionId    | **integer.** The ID of the individual buy or sell execution. If not specified, returns all._optional._                                                                                                                       |

### Response

```javascript
[
  {
    OMSId: 1,
    ExecutionId: 5234,
    TradeId: 4506,
    OrderId: 62016,
    AccountId: 20,
    AccountName: "aputest",
    SubAccountId: 0,
    ClientOrderId: 0,
    InstrumentId: 1,
    Side: "Sell",
    OrderType: "Limit",
    Quantity: 0.88576,
    RemainingQuantity: 0.0,
    Price: 25000.0,
    Value: 22144.0,
    CounterParty: "200",
    OrderTradeRevision: 1,
    Direction: "NoChange",
    IsBlockTrade: false,
    Fee: 0.0,
    FeeProductId: 0,
    OrderOriginator: 18,
    UserName: "aputest",
    TradeTime: 638122111809220337,
    TradeTimeMS: 1676614380922,
    MakerTaker: "Maker",
    AdapterTradeId: 0,
    InsideBid: 8.0,
    InsideBidSize: 2.0,
    InsideAsk: 25000.0,
    InsideAskSize: 1.0,
    IsQuote: false,
    CounterPartyClientUserId: 1,
    NotionalProductId: 1,
    NotionalRate: 1.0,
    NotionalValue: 22144.0,
    NotionalHoldAmount: 0,
  },
  {
    OMSId: 1,
    ExecutionId: 5232,
    TradeId: 4505,
    OrderId: 62016,
    AccountId: 20,
    AccountName: "aputest",
    SubAccountId: 0,
    ClientOrderId: 0,
    InstrumentId: 1,
    Side: "Sell",
    OrderType: "Limit",
    Quantity: 0.01,
    RemainingQuantity: 0.88576,
    Price: 25000.0,
    Value: 250.0,
    CounterParty: "200",
    OrderTradeRevision: 1,
    Direction: "NoChange",
    IsBlockTrade: false,
    Fee: 0.0,
    FeeProductId: 0,
    OrderOriginator: 18,
    UserName: "aputest",
    TradeTime: 638122111287631374,
    TradeTimeMS: 1676614328763,
    MakerTaker: "Maker",
    AdapterTradeId: 0,
    InsideBid: 8.0,
    InsideBidSize: 2.0,
    InsideAsk: 25000.0,
    InsideAskSize: 1.0,
    IsQuote: false,
    CounterPartyClientUserId: 1,
    NotionalProductId: 1,
    NotionalRate: 1.0,
    NotionalValue: 250.0,
    NotionalHoldAmount: 0,
  },
];
```

```http
[
  {
    OMSId: 1,
    ExecutionId: 5234,
    TradeId: 4506,
    OrderId: 62016,
    AccountId: 20,
    AccountName: "aputest",
    SubAccountId: 0,
    ClientOrderId: 0,
    InstrumentId: 1,
    Side: "Sell",
    OrderType: "Limit",
    Quantity: 0.88576,
    RemainingQuantity: 0.0,
    Price: 25000.0,
    Value: 22144.0,
    CounterParty: "200",
    OrderTradeRevision: 1,
    Direction: "NoChange",
    IsBlockTrade: false,
    Fee: 0.0,
    FeeProductId: 0,
    OrderOriginator: 18,
    UserName: "aputest",
    TradeTime: 638122111809220337,
    TradeTimeMS: 1676614380922,
    MakerTaker: "Maker",
    AdapterTradeId: 0,
    InsideBid: 8.0,
    InsideBidSize: 2.0,
    InsideAsk: 25000.0,
    InsideAskSize: 1.0,
    IsQuote: false,
    CounterPartyClientUserId: 1,
    NotionalProductId: 1,
    NotionalRate: 1.0,
    NotionalValue: 22144.0,
    NotionalHoldAmount: 0,
  },
  {
    OMSId: 1,
    ExecutionId: 5232,
    TradeId: 4505,
    OrderId: 62016,
    AccountId: 20,
    AccountName: "aputest",
    SubAccountId: 0,
    ClientOrderId: 0,
    InstrumentId: 1,
    Side: "Sell",
    OrderType: "Limit",
    Quantity: 0.01,
    RemainingQuantity: 0.88576,
    Price: 25000.0,
    Value: 250.0,
    CounterParty: "200",
    OrderTradeRevision: 1,
    Direction: "NoChange",
    IsBlockTrade: false,
    Fee: 0.0,
    FeeProductId: 0,
    OrderOriginator: 18,
    UserName: "aputest",
    TradeTime: 638122111287631374,
    TradeTimeMS: 1676614328763,
    MakerTaker: "Maker",
    AdapterTradeId: 0,
    InsideBid: 8.0,
    InsideBidSize: 2.0,
    InsideAsk: 25000.0,
    InsideAskSize: 1.0,
    IsQuote: false,
    CounterPartyClientUserId: 1,
    NotionalProductId: 1,
    NotionalRate: 1.0,
    NotionalValue: 250.0,
    NotionalHoldAmount: 0,
  },
];
```

The response is an array of objects, each element of which represents the account’s side of a trade (either buy or sell).

| Key                | Value                                                                                                                                                                                                              |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| OMSId              | **integer.** The ID of the Order Management System to which the account belongs.                                                                                                                                   |
| ExecutionId        | **integer.** The ID of this account's side of the trade. Every trade has two sides.                                                                                                                                |
| TradeId            | **integer.** The ID of the overall trade.                                                                                                                                                                          |
| OrderId            | **long integer.** The ID of the order causing the trade (buy or sell).                                                                                                                                             |
| AccountId          | **integer.** The ID of the account that made the trade (buy or sell).                                                                                                                                              |
| AccountName        | **string.** The Name of the account that made the trade (buy or sell).                                                                                                                                             |
| SubAccountId       | **integer.** Not currently used; reserved for future use. Defaults to 0.                                                                                                                                           |
| ClientOrderId      | **long integer.** An ID supplied by the client to identify the order (like a purchase order number). The _clientOrderId_ defaults to 0 if not supplied.                                                            |
| InstrumentId       | **integer.** The ID of the instrument being traded. An instrument comprises two products, for example Dollars and BitCoin.                                                                                         |
| Side               | **string.** One of the following potential sides of a trade: <br />**0** Buy<br />**1** Sell<br />**2** Short<br />**3** Unknown (an error condition)                                                              |
| OrderType          | **string.** One of the following potential sides of a trade: <br />Market<br />Limit<br />BlockTrade<br />StopMarket<br />StopLimit<br />TrailingStopLimit<br />StopMarket<br />TrailingStopMarket                 |
| Quantity           | **real.** The unit quantity of this side of the trade.                                                                                                                                                             |
| RemainingQuantity  | **real.** The number of units remaining to be traded by the order after this execution. This number is not revealed to the other party in the trade. This value is also known as "leave size" or "leave quantity." |
| Price              | **real.** The unit price at which the instrument traded.                                                                                                                                                           |
| Value              | **real.** The total value of the deal. The system calculates this as:<br />unit price X quantity executed.                                                                                                         |
| CounterParty       | **string.** The ID of the other party in a block trade. Usually, IDs are stated as integers; this value is an integer written as a string.                                                                         |
| OrderTradeRevision | **integer.** The revision number of this trade; usually 1.                                                                                                                                                         |
| Direction          | **integer.** The effect of the trade on the instrument's market price. One of:<br />**0** No change<br />**1** Uptick<br />**2** DownTick                                                                          |
| IsBlockTrade       | **Boolean.** A value of _true_ means that this trade was a block trade; a value of _false_ that it was not a block trade.                                                                                          |
| Fee                | **real.** Any fee levied against the trade by the Exchange.                                                                                                                                                        |
| FeeProductId       | **integer.** The ID of the product in which the fee was levied.                                                                                                                                                    |
| OrderOriginator    | **integer.** The ID of the user who initiated the trade.                                                                                                                                                           |
| UserName           | **integer.** The UserName of the user who initiated the trade.                                                                                                                                                     |
| TradeTimeMS        | **long integer.** The date and time that the trade took place, in milliseconds and POSIX format. All dates and times are UTC.                                                                                      |
| MakerTaker         | **string.** One of the following potential liquidity provider of a trade: <br />Maker<br />Taker<br />                                                                                                             |
| AdapterTradeId     | **integer.** The ID of the adapter of the overall trade.                                                                                                                                                           |
| InsideBid          | **real.** The best (highest) price level of the buy side of the book at the time of the trade.                                                                                                                     |
| InsideBidSize      | **real.** The quantity of the best (highest) price level of the buy side of the book at the time of the trade.                                                                                                     |
| InsideAsk          | **real.** The best (lowest) price level of the sell side of the book at the time of the trade.                                                                                                                     |
| InsideAskSize      | **real.** The quantity of the best (lowest) price level of the sell side of the book at the time of the trade.                                                                                                     |
| TradeTime          | **long integer.** The date and time that the trade took place, in C# Ticks. All dates and times are UTC.                                                                                                           |
