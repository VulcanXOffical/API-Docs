## UpdateInstrument

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Updates (changes) an instrument definition on the Order Management System. The values for *omsId* and *instrumentId* cannot be changed; the balance of the values can be updated.

### Request

```json
{
    "omsId": 0,
    "instrumentId": 0,
    "symbol": null,
    "product1":3 ,
    "product1Symbol": "LTC",
    "product2": 8,
    "product2Symbol": "NZD",
    "instrumentType": 0,
    "venueInstrumentId": 0,
    "venueId": 0,
    "sortIndex": 0,
    "sessionStatus": 0,
    "previousSessionStatus": 0,
    "sessionStatusDateTime": "0001-01-01T00:00:00",
    "selfTradePrevention": false,
    "quantityIncrement": 0.0,
    "priceIncrement": 1.0}

```

| Key                   | Value                                                        |
| --------------------- | ------------------------------------------------------------ |
| omsId                 | **integer.** The ID of the Order Management System on which you are changing the instrument. |
| instrumentId          | **integer.** The ID of the instrument being changed. You can get a list of all instruments on the Exchange by using the call **GetInstruments.** |
| symbol                | **string.** The trading symbol of the instrument. By convention, this is a combination of the symbols for the two component products that are traded for one another; for example, ABCBTC. |
| product1              | **integer.** The ID of the first component product that forms the instrument. |
| product1Symbol        | **string.** The trading symbol for product 1.                |
| product2              | **integer.** The ID of the second component product that forms the instrument. |
| product2Symbol        | **string.** The trading symbol for product 2.                |
| instrumentType        | **integer.** A number representing the type of the instrument. All instrument types currently are *standard* &mdash; an exchange of one product for another &mdash; or *unknown,* an error condition. This may expand to new instrument types in the future.<br />**0** Unknown (an error condition)<br />**1** Standard |
| venueInstrumentId     | **integer.** A venue instrument is created at the Exchange level as an instrument "template" for adding new instruments to the Exchange. *VenueInstrumentId* is the ID of the venue instrument behind the instrument being created. |
| venueId               | **integer.** The ID of the trading venue on which the instrument trades. |
| sortIndex             | **integer.** The numerical position in which to sort a returned list of instruments on a visual display. |
| sessionStatus         | **integer.** Is the market for this instrument currently open and operational? One of:<br />**0** Unknown<br />**1** Running<br />**2** Paused<br />**3** Stopped<br />**4** Starting |
| previousSessionStatus | **integer.** What was the previous session status for this instrument? One of:<br/>**0** Unknown<br />**1** Running<br />**2** Paused<br />**3** Stopped<br />**4** Starting |
| sessionStatusDateTime | **string.** The time and date at which the session status was reported, in Microsoft Ticks format and UTC time zone. |
| selfTradePrevention   | **Boolean.** An account that is trading with itself still incurs fees. If this instrument prevents an account from trading the instrument with itself, the value returns *true*; otherwise defaults to *false*. |
| quantityIncrement     | **real.** The smallest tradeable increment of the instrument. For example, for BTCUSD, the quantity increment might be 0.0005, but for ETHUSD, the quantity increment might be 50. |
| priceIncrement        | **real.** The smallest price amount by which the instrument can rise or fall in the market. |

### Response

```json
{
    "Id": 1,
    "RejectMessage":"Reason for reject."
}
```

| Key           | Value                                                        |
| ------------- | ------------------------------------------------------------ |
| Id            | **integer.** The ID of the instrument you have just updated (or attempted to update). |
| RejectMessage | **string.** If the update was rejected by the system, this value holds a human-readable explanation. If the update was accepted, this value will be empty. |




