## AddEditExchangeInstrument

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** **Synchronous**

Adds a new instrument (and its market) to an existing Exchange.

### Request

```json
{
    "omsId": 1,
    "exchangeServiceId": "V2ExchangeCore",
    "exchangeId": 0,
    "instrumentId": 0,
    "productPairType": 0,
    "orderBookType": 0,
    "productPairId": 0,
    "product1Id": 0,
    "product2Id": 0,
    "minimumQuantity": 0.0,
    "priceIncrement": 0.0,
    "symbol": "",
    "selfTradePrevention": true,
    "priceCollarThreshold": 0.0,
    "priceCollarPercent": 0.0,
    "priceCollarEnabled": true,
    "priceFloorLimit": 0.0,
    "priceFloorLimitEnabled": true,
    "priceCeilingLimit": 0.0,
    "priceCeilingLimitEnabled": true,
    "createWithMarketRunning": true
}
```
Required key-value pairs are marked; other KVPs are optional in the Request.

| Key                      | Value                                                        |
| ------------------------ | ------------------------------------------------------------ |
| omsId                    | **integer.** REQUIRED The ID of the Order Management System on which the instrument will be created.  |
| exchangeServiceId        | **string.** The name of the matching engine on which the new instrument will be traded. |
| exchangeId               | **integer.** The ID of the AlphaPoint Exchange on which the instrument will be traded. |
| instrumentId             | **integer.** REQUIRED The value for *instrumentId* is determined by the system. Set this value to 0 when making the Request; the system responds with the assigned ID. |
| productPairType          | **integer.** A *product pair* is the same as *instrument.* The value of *productPairType* is an integer representing the type of instrument. All instrument types currently are *standard* (an exchange of one product for another), or *unknown* (an error condition). This may expand to new types in the future. One of:<br />**0** Unknown (an error condition)<br />**1** Standard |
| orderBookType            | **integer.** The type of order book for the Exchange. One of <br />**0** Unknown (an error condition)<br />**1** Standard<br />**2** NoMatching<br />**3** Crossing                                                |
| productPairId            | **integer.** The value for *productPairId* is determined by the system. Set this value to 0 in the Request; the system responds with the assigned ID. |
| product1Id               | **integer.** The ID of the first product making up the instrument. For example, if the instrument is BTCUSD, BitCoin would be *product1* and the ID for the BitCoin asset would be *product1Id.* |
| product2Id               | **integer.** The ID of the second product making up the instrument. For example, if the instrument is BTCUSD, US Dollar would be *product2* and the ID for the USD asset would be *product2Id.* |
| minimumQuantity          | **real.** The minimum quantity in which the instrument is traded. For example, US Dollars cannot be traded in increments smaller than 1 cent (1/100 of a dollar); there is no half-cent denomination. |
| priceIncrement           | **real.** The smallest value by which the instrument can rise or fall on the Exchange. This is different from the number of decimal places in which the instrument is priced.                                                    |
| symbol                   | **string.** REQUIRED The alphanumeric characters designating the instrument; for example BTCUSD for the instrument BitCoin/US Dollars. |
| selfTradePrevention      | **Boolean.** An account trading with itself may still incur fees. If this instrument prevents an account from trading the instrument with itself, the value is *true,* otherwise, the value is *false.* |
| priceCollarThreshold     | **real.** A price threshold amount beyond the current market price that determines whether a put or call on the instrument is a collar strategy. |
| priceCollarPercent       | **real.** A price threshold percentage beyond the current market price that determines whether a put or a call on the instrument is a collar strategy. |
| priceCollarEnabled       | **Boolean.** A value of *true* enables purchasing out-of-the-money put options or writing out-of-the-money call options on the instrument. A value of *false* prevents collar strategies on the instrument. |
| priceFloorLimit          | **real.** A limit for the lowest acceptable price for the instrument on the Exchange, as determined by the Exchange operator. |
| priceFloorLimitEnabled   | **Boolean.** A value of *true* enables the floor limit, and halts trading in the instrument if the limit is reached. The Exchange operator is also notified by system via email. |
| priceCeilingLimit        | **real.** A limit for the highest acceptable price for the instrument on the Exchange, as determined by the Exchange operator. |
| priceCeilingLimitEnabled | **Boolean.** A value of *true* enables the ceiling limit, and halts trading in the instrument if the limit is reached. The Exchange operator is also notified by the system via email. |
| createWithMarketRunning  | **Boolean.** A value of *true* means that the new instrument is created and immediately available on the operating market. A value of *false* means that the new instrument must wait for the market to be paused or halted, and will become available once the market restarts. |

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




