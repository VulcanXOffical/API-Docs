## GetInstruments

**Category:** Trading<br />
**Permissions:** Public<br />
**Call Type:** Synchronous

Retrieves a list of instruments available on the exchange. An instrument is something that can be traded in the exchange.

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

//Get all enabled instruments only
await apex.RPCPromise('GetInstruments',{
OMSId: 1
})

//Get all instruments including the disabled ones
await apex.RPCPromise('GetInstruments',{
OMSId: 1,
InstrumentState: "both"
})

//Get all disabled/inactive instruments only
await apex.RPCPromise('GetInstruments',{
OMSId: 1
InstrumentState: "inactive"
})
```

```http
POST /AP/GetInstruments HTTP/1.1
Host: hostname goes here...
Content-Type: application/json
Content-Length: 20
//Get all enabled instruments only
{
    "OMSId": 1
}

//Get all instruments including the disabled ones
{
    "OMSId": 1
    "InstrumentState": "both"
}

//Get all disabled/inactive instruments only
{
    "OMSId": 1
    "InstrumentState": "inactive"
}
```

| Key             | Value                                                                                                                                                                                                                                     |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| OMSId           | **integer**. The ID of the Order Management System on which the instruments are available._required._                                                                                                                                     |
| InstrumentState | **string**. Filters the results, you can include disabled instruments in the results, or you can just get disabled instruments if you want. If not set, **GetInstruments** will only return **enabled or active** instruments._optional._ |

### Response

```javascript
[
  {
    OMSId: 1,
    InstrumentId: 2,
    Symbol: "ETHUSD",
    Product1: 4,
    Product1Symbol: "ETH",
    Product2: 1,
    Product2Symbol: "USD",
    InstrumentType: "Standard",
    VenueInstrumentId: 2,
    VenueId: 1,
    SortIndex: 0,
    SessionStatus: "Running",
    PreviousSessionStatus: "Stopped",
    SessionStatusDateTime: "2023-01-23T04:49:21.699Z",
    SelfTradePrevention: true,
    QuantityIncrement: 0.0001,
    PriceIncrement: 0.00000001,
    MinimumQuantity: 0.0001,
    MinimumPrice: 0.00000001,
    VenueSymbol: "ETHUSD",
    IsDisable: false,
    MasterDataId: 0,
    PriceCollarThreshold: 0.0,
    PriceCollarPercent: 0.0,
    PriceCollarEnabled: false,
    PriceFloorLimit: 0.0,
    PriceFloorLimitEnabled: false,
    PriceCeilingLimit: 0.0,
    PriceCeilingLimitEnabled: false,
    CreateWithMarketRunning: true,
    AllowOnlyMarketMakerCounterParty: false,
    PriceCollarIndexDifference: 10.0,
    PriceCollarConvertToOtcEnabled: false,
    PriceCollarConvertToOtcClientUserId: 0,
    PriceCollarConvertToOtcAccountId: 0,
    PriceCollarConvertToOtcThreshold: 0.0,
    OtcConvertSizeThreshold: 0.0,
    OtcConvertSizeEnabled: false,
    OtcTradesPublic: true,
    PriceTier: 0,
  },
  {
    OMSId: 1,
    InstrumentId: 3,
    Symbol: "TBTCUSD",
    Product1: 3,
    Product1Symbol: "TBTC",
    Product2: 1,
    Product2Symbol: "USD",
    InstrumentType: "Standard",
    VenueInstrumentId: 3,
    VenueId: 1,
    SortIndex: 0,
    SessionStatus: "Stopped",
    PreviousSessionStatus: "Paused",
    SessionStatusDateTime: "2022-10-25T17:56:32.218Z",
    SelfTradePrevention: true,
    QuantityIncrement: 0.001,
    PriceIncrement: 0.001,
    MinimumQuantity: 0.001,
    MinimumPrice: 0.00000001,
    VenueSymbol: "TBTCUSD",
    IsDisable: false,
    MasterDataId: 0,
    PriceCollarThreshold: 0.0,
    PriceCollarPercent: 0.0,
    PriceCollarEnabled: false,
    PriceFloorLimit: 0.0,
    PriceFloorLimitEnabled: false,
    PriceCeilingLimit: 0.0,
    PriceCeilingLimitEnabled: false,
    CreateWithMarketRunning: true,
    AllowOnlyMarketMakerCounterParty: false,
    PriceCollarIndexDifference: 0.0,
    PriceCollarConvertToOtcEnabled: false,
    PriceCollarConvertToOtcClientUserId: 0,
    PriceCollarConvertToOtcAccountId: 0,
    PriceCollarConvertToOtcThreshold: 0.0,
    OtcConvertSizeThreshold: 0.0,
    OtcConvertSizeEnabled: false,
    OtcTradesPublic: true,
    PriceTier: 0,
  },
];
```

```http
[
    {
        "OMSId": 1,
        "InstrumentId": 2,
        "Symbol": "ETHUSD",
        "Product1": 4,
        "Product1Symbol": "ETH",
        "Product2": 1,
        "Product2Symbol": "USD",
        "InstrumentType": "Standard",
        "VenueInstrumentId": 2,
        "VenueId": 1,
        "SortIndex": 0,
        "SessionStatus": "Running",
        "PreviousSessionStatus": "Stopped",
        "SessionStatusDateTime": "2023-01-23T04:49:21.699Z",
        "SelfTradePrevention": true,
        "QuantityIncrement": 0.0001000000000000000000000000,
        "PriceIncrement": 0.0000000100000000000000000000,
        "MinimumQuantity": 0.0001000000000000000000000000,
        "MinimumPrice": 0.0000000100000000000000000000,
        "VenueSymbol": "ETHUSD",
        "IsDisable": false,
        "MasterDataId": 0,
        "PriceCollarThreshold": 0.0000000000000000000000000000,
        "PriceCollarPercent": 0.0000000000000000000000000000,
        "PriceCollarEnabled": false,
        "PriceFloorLimit": 0.0000000000000000000000000000,
        "PriceFloorLimitEnabled": false,
        "PriceCeilingLimit": 0.0000000000000000000000000000,
        "PriceCeilingLimitEnabled": false,
        "CreateWithMarketRunning": true,
        "AllowOnlyMarketMakerCounterParty": false,
        "PriceCollarIndexDifference": 10.000000000000000000000000000,
        "PriceCollarConvertToOtcEnabled": false,
        "PriceCollarConvertToOtcClientUserId": 0,
        "PriceCollarConvertToOtcAccountId": 0,
        "PriceCollarConvertToOtcThreshold": 0.0000000000000000000000000000,
        "OtcConvertSizeThreshold": 0.0000000000000000000000000000,
        "OtcConvertSizeEnabled": false,
        "OtcTradesPublic": true,
        "PriceTier": 0
    },
    {
        "OMSId": 1,
        "InstrumentId": 3,
        "Symbol": "TBTCUSD",
        "Product1": 3,
        "Product1Symbol": "TBTC",
        "Product2": 1,
        "Product2Symbol": "USD",
        "InstrumentType": "Standard",
        "VenueInstrumentId": 3,
        "VenueId": 1,
        "SortIndex": 0,
        "SessionStatus": "Stopped",
        "PreviousSessionStatus": "Paused",
        "SessionStatusDateTime": "2022-10-25T17:56:32.218Z",
        "SelfTradePrevention": true,
        "QuantityIncrement": 0.0010000000000000000000000000,
        "PriceIncrement": 0.0010000000000000000000000000,
        "MinimumQuantity": 0.0010000000000000000000000000,
        "MinimumPrice": 0.0000000100000000000000000000,
        "VenueSymbol": "TBTCUSD",
        "IsDisable": false,
        "MasterDataId": 0,
        "PriceCollarThreshold": 0.0000000000000000000000000000,
        "PriceCollarPercent": 0.0000000000000000000000000000,
        "PriceCollarEnabled": false,
        "PriceFloorLimit": 0.0000000000000000000000000000,
        "PriceFloorLimitEnabled": false,
        "PriceCeilingLimit": 0.0000000000000000000000000000,
        "PriceCeilingLimitEnabled": false,
        "CreateWithMarketRunning": true,
        "AllowOnlyMarketMakerCounterParty": false,
        "PriceCollarIndexDifference": 0.0000000000000000000000000000,
        "PriceCollarConvertToOtcEnabled": false,
        "PriceCollarConvertToOtcClientUserId": 0,
        "PriceCollarConvertToOtcAccountId": 0,
        "PriceCollarConvertToOtcThreshold": 0.0000000000000000000000000000,
        "OtcConvertSizeThreshold": 0.0000000000000000000000000000,
        "OtcConvertSizeEnabled": false,
        "OtcTradesPublic": true,
        "PriceTier": 0
    }
 ]
```

The response for **GetInstruments** is an array of objects listing all the instruments available on the Order Management System.

| Key                                 | Value                                                                                                                                                                                                                                                                                        |
| ----------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| OMSId                               | **integer.** The ID of the Order Management System on which the instrument is traded.                                                                                                                                                                                                        |
| instrumentId                        | **integer.** The ID of the instrument.                                                                                                                                                                                                                                                       |
| Symbol                              | **string.** Trading symbol of the instrument, for example BTCUSD.                                                                                                                                                                                                                            |
| Product1                            | **integer.** The ID of the first product comprising the instrument.                                                                                                                                                                                                                          |
| Product1Symbol                      | **string.** The symbol for Product 1 on the trading venue. For example, BTC.                                                                                                                                                                                                                 |
| Product2                            | **integer.** The ID of the second product comprising the instrument.                                                                                                                                                                                                                         |
| Product2Symbol                      | **string.** The symbol for Product 2 on the trading venue. For example, USD.                                                                                                                                                                                                                 |
| InstrumentType                      | **integer.** A number representing the type of the instrument. All instrument types currently are _standard_, an exchange of one product for another (or _unknown_, an error condition), but this may expand to new types in the future.<br />0 Unknown (an error condition)<br />1 Standard |
| VenueInstrumentId                   | **integer** A venue instrument is created at the exchange level as an instrument "template" for adding new instruments to the exchange. This is the ID of the venue instrument behind the instrument being requested.                                                                        |
| VenueId                             | **integer.** The ID of the trading venue on which the instrument trades.                                                                                                                                                                                                                     |
| SortIndex                           | **integer.** The numerical position in which to sort the returned list of instruments on a visual display. Since this call returns information about a single instrument, _SortIndex_ should return 0.                                                                                       |
| SessionStatus                       | **string.** or **integer.** Is the market for this instrument currently open and operational? Returns one of:<br />0 Unknown<br />1 Running<br />2 Paused<br />3 Stopped<br />4 Starting                                                                                                     |
| PreviousSessionStatus               | **string.** or **integer.** What was the previous session status for this instrument? One of:<br />0 Unknown<br />1 Running<br />2 Paused<br />3 Stopped<br />4 Starting                                                                                                                     |
| SessionStatusDateTime               | **string.** The time and date at which the session status was reported, in Microsoft Ticks format.                                                                                                                                                                                           |
| SelfTradePrevention                 | **Boolean.** An account that is trading with itself still incurs fees. If this instrument prevents an account from trading the instrument with itself, the value returns _true_; otherwise defaults to _false_.                                                                              |
| QuantityIncrement                   | **real.** The smallest tradeable increment of the instrument. For example, for BTCUSD, the quantity increment might be 0.0005, but for ETHUSD, the quantity increment might be 50.                                                                                                           |
| PriceIncrement                      | **real.** The amount by which the instrument can rise or fall in the market.                                                                                                                                                                                                                 |
| priceCollarIndexDifference          | **decimal.** The percent different from the index price that an order is allowed to execute at. Anything falling outside of the index price +/- (1 + PriceCollarIndexDifference) will be collared                                                                                            |
| PriceCollarConvertToOtcEnabled      | **bool.** Turns on/off conversion of collared orders to block trades                                                                                                                                                                                                                         |
| PriceCollarConvertToOtcClientUserId | **int.** Internal System UserId to assign the collared otc orders to. Should alwaays be 1 in current implementation (default)                                                                                                                                                                |
| PriceCollarConvertToOtcAccountId    | **int.** Account Id to assign the collared orders to. This will effectively be a liability account that will need to have working block trades managed by operator.                                                                                                                          |
| PriceCollarConvertToOtcThreshold    | **decimal.** Threshold of remaining size of order to convert to block trade. If collared order does not have remaining quantity above this threshold the remainder will be cancelled.                                                                                                        |
| OtcConvertSizeEnabled               | **bool.** Turns on/off auto conversion of 'large' limit orders converted to block trade orders upon receipt by the matching engine                                                                                                                                                           |
| OtcConvertSizeThreshold             | **decimal.** Threshold to convert limit order quantity to block trade automatically for discovery by block trade market participants                                                                                                                                                         |
| OtcTradesPublic                     | **bool** If set to true, OTC trades will affect instrument Level1 data(price, volume), will reflect in the chart.                                                                                                                                                                            |
| PriceTier                           | **integer.** The price tier the instrument is under.                                                                                                                                                                                                                                         |
