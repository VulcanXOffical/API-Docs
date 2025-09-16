## AddInstrument

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Defines a new instrument on a specific Order Management System.

The two component products that form the instrument must both already exist on the Exchange. To create a product, see **AddProduct.** 

### Request

```json
{
    "OMSId": 1,
    "InstrumentId": 1,
    "Symbol": "ABCBTC",
    "Product1": 1,
    "Product1Symbol": "BTC", 
    "Product2": 26,
    "Product2Symbol": "ABCs",
    "InstrumentType": 1,
    "VenueInstrumentId": 1,
    "VenueId": 1,
    "SortIndex": 1,
    "SessionStatus ": 1,
    "PreviousSessionStatus": 2,
    "SessionStatusDateTime": "2019-04-10T04:00:00.000Z",
    "SelfTradePrevention": true,
    "QuantityIncrement": 1.0,
    "PriceIncrement": 1.0
}
```

| Key                   | Value                                                        |
| --------------------- | ------------------------------------------------------------ |
| OMSId                 | **integer.** The ID of the Order Management System to which you are adding the instrument. |
| InstrumentId          | **integer.** The ID of the instrument being added. Because the Exchange assigns instrument IDs, set this to 0 in the Request. The ID of the new instrument is returned by the Response as the value of *Id.* |
| symbol                | **string.** The trading symbol of the instrument. By convention, this is a combination of the symbols for the two component products that are traded for one another; for example, ABCBTC. |
| Product1              | **integer.** The ID of the first component product that forms the instrument. |
| Product1Symbol        | **string.** The trading symbol for product 1.                |
| Product2              | **integer.** The ID of the second component product that forms the instrument. |
| Product2Symbol        | **string.** The trading symbol for product 2.                |
| InstrumentType        | **integer.** A number representing the type of the instrument. All instrument types currently are *standard* &mdash; an exchange of one product for another &mdash; or *unknown,* an error condition. This may expand to new instrument types in the future.<br />**0** Unknown (an error condition)<br />**1** Standard |
| VenueInstrumentId     | **integer.** A venue instrument is created at the Exchange level as an instrument "template" for adding new instruments to the Exchange. *VenueInstrumentId* is the ID of the venue instrument behind the instrument being created. |
| VenueId               | **integer.** The ID of the trading venue on which the instrument trades. |
| SortIndex             | **integer.** The numerical position in which to sort a returned list of instruments on a visual display. |
| SessionStatus         | **integer.** Is the market for this instrument currently open and operational? One of:<br />**0** Unknown<br />**1** Running<br />**2** Paused<br />**3** Stopped<br />**4** Starting |
| PreviousSessionStatus | **integer.** What was the previous session status for this instrument? One of:<br/>**0** Unknown<br />**1** Running<br />**2** Paused<br />**3** Stopped<br />**4** Starting |
| SessionStatusDateTime | **string.** The time and date at which the session status was reported, in Microsoft Ticks format and UTC time zone. |
| SelfTradePrevention   | **Boolean.** An account that is trading with itself still incurs fees. If this instrument prevents an account from trading the instrument with itself, the value returns *true*; otherwise defaults to *false*. |
| QuantityIncrement     | **real.** The smallest tradeable increment of the instrument. For example, for BTCUSD, the quantity increment might be 0.0005, but for ETHUSD, the quantity increment might be 50. |
| PriceIncrement        | **real.** The smallest price amount by which the instrument can rise or fall in the market. |

### Response

```json
{
    "Id": 1,
    "RejectMessage": ""
}
```

| Key           | Value                                                        |
| ------------- | ------------------------------------------------------------ |
| Id            | **integer.** The ID assigned to the newly created instrument by the Exchange. |
| RejectMessage | **string.** If the creation of the instrument was rejected by the Exchange, the value of this key provides information. Otherwise, empty. |


