## SendMarginQuote

**Category:** User<br />**Permissions:** Operator, Trading<br />**Call Type:** Asynchronous

Sends a margin quote to the Order Management System.

<aside class="notice"><strong>Note:</strong> This is an asynchronous call.</aside>


### Request

```json
{
    "omsId": 0,
    "quoteId": 0,
    "clientQuoteId": 0,
    "receiveTimeUtcTicks": 0,
    "accountId": 0,
    "productId": 0,
    "term": 0,
    "orderType": 0,
    "side": 0,
    "tif": 0,
    "quantity": 0.0,
    "rate": 0.0,
    "orderExpirationDateTime": 0,
    "enteredBy": 0
}
```

| Key                     | Value                                                        |
| ----------------------- | ------------------------------------------------------------ |
| omsId                   | **integer.** The ID of the Order Management System where the quote is sent. |
| quoteId                 | **long integer.** Set the value of *quoteId* to 0 in the Request. The Response returns the value assigned by the system in the key-value pair *MarginQuoteId.* |
| clientQuoteId           | **long integer.** The ID of the quote as assigned by the user (like a purchase order number). |
| receiveTimeUtcTicks     | **long integer.**  A time in POSIX format. Set this to 0 in the Request; the system will add it to the margin quote when it is accepted.      |
| accountId               | **integer.** The ID of the account sending the quote.        |
| productId               | **integer.** The ID of the product being quoted.             |
| term                    | **integer.** The term of the lend or borrow, in days. |
| orderType               | **integer.** A number representing the nature of the order (quote). One of:<br />**0** Unknown<br />**1** Market <br />**2** Limit<br />**3** StopMarket<br />**4** StopLimit<br />**5** TrailingStopMarket<br />**6** TrailingStopLimit<br />**7** BlockTrade |
| side                    | **integer.** A number representing one of the following potential sides of a trade:<br />**0** Buy<br />**1** Sell<br />**2** Short<br />**3** Unknown (an error condition) |
| tif                     | **integer.** Time-in-Force. An integer that represents the period during which the quote is executable. One of:<br />**0** Unknown (an error condition)<br />**1** GTC (good 'til canceled, the default)<br />**2** OPG (execute as close to opening price as possible)<br />**3** IOC (immediate or cancel)<br />**4** FOK (fill or kill immediately)<br />**5** GTX (good 'til executed)<br />**6** GTD (good 'til date) |
| quantity                | **real.** The size of the quote in product units.            |
| rate                    | **real.** The rate of the borrow, usually stated as the rate per day.        |
| orderExpirationDateTime | **long integer.** The time and date that the order expires, in POSIX format. |
| enteredBy               | **integer.** The ID of the user who entered the quote.       |

### Response

```json
{
    "status": "Accepted",
    "errormsg": "",
    "errorcode": 101,
    "MarginQuoteId": 1
}
```

| Key           | Value                                                        |
| ------------- | ------------------------------------------------------------ |
| status        | **string.** Either the value "Accepted" or the value "Rejected," which signify whether the quote was accepted or rejected by the exchange. |
| errormsg      | **string.** A successful receipt of the quote returns null; the *errormsg* parameter for an unsuccessful receipt returns one of the following messages:<br/>Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode     | **integer.** A successful receipt returns 0. An unsuccessful receipt returns one of the errorcodes shown in the errormsg list.
| MarginQuoteId | **long integer.** The ID for the margin quote that is assigned by the OMS. |


