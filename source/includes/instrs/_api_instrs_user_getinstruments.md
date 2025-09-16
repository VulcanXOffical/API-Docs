## GetInstruments

**Category:** User<br />**Permissions:** Public<br />**Call Type:** Synchronous

Retrieves a list of instruments available on the exchange. An instrument is a pair of exchanged products (or fractions of them) such as US dollars and BitCoin. 

### Request

```json
{
	"OMSId":  1
}
```

| Key   | Value                                                        |
| ----- | ------------------------------------------------------------ |
| OMSId | **integer**. The ID of the Order Management System on which the instruments are available. |

### Response

```json
[
    {
        "omsId":0 ,
        "instrumentId": 0,
        "symbol": "",
        "product1": 0,
        "product1Symbol": "",
        "product2": 0,
        "product2Symbol": "",
        "instrumentType": 0,
        "venueInstrumentId": 0,
        "venueId":0,"sortIndex": 0,
        "sessionStatus": 0,
        "previousSessionStatus": 0,
        "sessionStatusDateTime": "0001-01-01T00:00:00",
        "selfTradePrevention": false,
        "quantityIncrement": 0.0,
        "priceIncrement": 0.0,
        "priceCollarIndexDifference": 0.0,
        "priceCollarConvertToOtcEnabled": false,
        "priceCollarConvertToOtcClientUserId": 1,
        "priceCollarConvertToOtcAccountId": 0,
        "priceCollarConvertToOtcThreshold": 0.0,
        "otcConvertSizeEnabled": false,
        "otcConvertSizeThreshold": 0.0,
    },
]
```

The response for **GetInstruments** is an array of objects listing all the instruments available on the Order Management System.

| Key                   | Value                                                        |
| --------------------- | ------------------------------------------------------------ |
| omsId                 | **integer.** The ID of the Order Management System on which the instrument is traded. |
| instrumentId          | **integer.** The ID of the instrument.                       |
| symbol                | **string.** Trading symbol of the instrument, for example BTCUSD. |
| product1              | **integer.** The ID of the first product comprising the instrument. |
| product1Symbol        | **string.** The symbol for Product 1 on the trading venue. For example, BTC. |
| product2              | **integer.** The ID of the second product comprising the instrument. |
| product2Symbol        | **string.** The symbol for Product 2 on the trading venue. For example, USD. |
| instrumentType        | **integer.** A number representing the type of the instrument. All instrument types currently are *standard*, an exchange of one product for another (or *unknown*, an error condition), but this may expand to new types in the future.<br />0 Unknown (an error condition)<br />1 Standard |
| venueInstrumentId     | **integer** A venue instrument is created at the exchange level as an instrument "template" for adding new instruments to the exchange. This is the ID of the venue instrument behind the instrument being requested. |
| venueId               | **integer.** The ID of the trading venue on which the instrument trades. |
| sortIndex             | **integer.** The numerical position in which to sort the returned list of instruments on a visual display. Since this call returns information about a single instrument, *SortIndex* should return 0. |
| sessionStatus         | **integer.** Is the market for this instrument currently open and operational? Returns one of:<br />0 Unknown<br />1 Running<br />2 Paused<br />3 Stopped<br />4 Starting |
| previousSessionStatus | **string.** What was the previous session status for this instrument? One of:<br />0 Unknown<br />1 Running<br />2 Paused<br />3 Stopped<br />4 Starting |
| sessionStatusDateTime | **string.**  The time and date at which the session status was reported, in Microsoft Ticks format. |
| selfTradePrevention   | **Boolean.** An account that is trading with itself still incurs fees. If this instrument prevents an account from trading the instrument with itself, the value returns *true*; otherwise defaults to *false*. |
| quantityIncrement     | **real.** The smallest tradeable increment of the instrument. For example, for BTCUSD, the quantity increment might be 0.0005, but for ETHUSD, the quantity increment might be 50. |
| priceIncrement        | **real.** The amount by which the instrument can rise or fall in the market.  |
| priceCollarIndexDifference | **decimal.** The percent different from the index price that an order is allowed to execute at. Anything falling outside of the index price +/- (1 + PriceCollarIndexDifference) will be collared |
| priceCollarConvertToOtcEnabled | **bool.** Turns on/off conversion of collared orders to block trades |
| priceCollarConvertToOtcClientUserId | **int.** Internal System UserId to assign the collared otc orders to. Should alwaays be 1 in current implementation (default) |
| priceCollarConvertToOtcAccountId | **int.** Account Id to assign the collared orders to. This will effectively be a liability account that will need to have working block trades managed by operator. |
| priceCollarConvertToOtcThreshold | **decimal.** Threshold of remaining size of order to convert to block trade. If collared order does not have remaining quantity above this threshold the remainder will be cancelled. |
| otcConvertSizeEnabled | **bool.** Turns on/off auto conversion of 'large' limit orders converted to block trade orders upon receipt by the matching engine |
| otcConvertSizeThreshold | **decimal.** Threshold to convert limit order quantity to block trade automatically for discovery by block trade market participants |