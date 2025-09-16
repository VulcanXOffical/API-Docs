## GetOrderFee

**Category:** Trading<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

Returns an estimate of the transaction/trading fee for a specific order side, instrument, and order type. An exchange operator decides and sets the fees for each instrument.

The exchange generally deducts fees from the "receiving" side of the trade (although an operator can modify this). There are two products in every trade (and in every instrument); for example, the instrument BTCUSD comprises a BitCoin product and a US dollar product. Placing a buy order on the book causes fees to be deducted from Product 1, in this case, BitCoin; placing a sell order causes fees to be deducted from Product 2, in this case, US dollar.

A user with Trading permission can get fee estimates for any account that user is associated with and for any instrument or product that that account can trade; a user with Operator permission can get fee estimates for any account, instrument, or product.

If loyalty token is enabled and there is no market for the loyalty token, the system automatically uses 3rd party rates for the loyalty token market.

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("GetOrderFee", {
  OMSId: 1,
  AccountId: 9,
  InstrumentId: 1,
  Quantity: 0.5,
  Side: 0,
  Price: "10000",
  OrderType: 2,
  MakerTaker: "Maker",
});
```

```http
POST /AP/GetOrderFee HTTP/1.1
Host: hostname goes here...
aptoken: f7e2c811-a9db-454e-9c9e-77533baf92d9 //valid sessiontoken
Content-Type: application/json
Content-Length: 177

{
  "OMSId": 1,
  "AccountId": 9,
  "InstrumentId": 1,
  "Quantity": 0.5,
  "Side": 0,
  "Price": "10000",
  "OrderType": 2,
  "MakerTaker": "Maker"
}
```

| Key          | Value                                                                                                                                                                                                                                                                                                                                         |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| OMSId        | **integer.** The ID of the Order Management System on which the trade would take place._required._                                                                                                                                                                                                                                            |
| AccountId    | **integer.** The ID of the account requesting the fee estimate. There can be account overrides, the exchange operator can decide to apply very specific fees to specific accounts, such as a discounted price to a specific account._required._                                                                                               |
| InstrumentId | **integer.** The ID of the instrument being or to be traded._required._                                                                                                                                                                                                                                                                       |
| Quantity     | **real.** The quantity or amount of the proposed trade for which the Order Management System would charge a fee._required._                                                                                                                                                                                                                   |
| Price        | **real.** The price at which the proposed trade would take place. Supply your price for a limit order; the exact price is difficult to know before execution._required._                                                                                                                                                                      |
| OrderType    | **integer..** The type of the proposed order. An operator can set fees per **OrderType**._required._<br /> One of:<br />0 Unknown<br />1 Market<br />2 Limit<br />3 StopMarket<br />4 StopLimit<br />5 TrailingStopMarket<br />6 TrailingStopLimit<br />7 BlockTrade<br />                                                                    |
| MakerTaker   | **integer.** Depending on the venue, there may be different fees for a maker (one who places the order on the books, either buy or sell) or taker (one who accepts the order, either buy or sell). If the user places a large order that is only partially filled, he is a partial maker._required._<br />0 Unknown<br />1 Maker<br />2 Taker |
| Side         | **integer.** Side of the trade. It will decide at which product will the fee be donominated. In APEX, the fee is charged in the incoming product by default._required._ One of:<br />0 Buy<br />1 Sell<br />2 Short<br />3 Unknown                                                                                                            |

### Response

```javascript
{
    "OrderFee": 0.0000100000000000000000000000,
    "ProductId": 2
}
```

```http
{
    "OrderFee": 0.0000100000000000000000000000,
    "ProductId": 2
}
```

| Key       | Value                                                                          |
| --------- | ------------------------------------------------------------------------------ |
| OrderFee  | **real.** The estimated fee for the trade as described.                        |
| ProductId | **integer.** The ID of the product (currency) in which the fee is denominated. |
