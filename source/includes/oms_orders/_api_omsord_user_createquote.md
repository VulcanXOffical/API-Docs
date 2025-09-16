## CreateQuote

**Category:** User<br />
**Permissions:** Operator, MarketMaker<br />
**Call Type:** Synchronous

**TK** call and response may change

Creates a quote. A quote expresses a willingness to buy or sell at a given price. Both a quote and an order will execute. Only a user with Operator or MarketMaker permission can create a quote.

<aside class="notice"><strong>Note:</strong> Quoting is not enabled for the retail end user of AlphaPoint software. Only registered market participants or market makers may quote.</aside>

### Request

```json
{
  "OMSId": 0,
  "AccountId": 0,
  "InstrumentId": 0,
  "Bid": 0,
  "BidQty": 0,
  "Ask": 0,
  "AskQty": 0,
}
```

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| OMSId        | **integer.** The ID of the Order Management System on which the quote is being created. *Required*. |
| AccountId    | **integer.** The ID of the account in which the quote is being created. If the call provides no AccountId, the system assumes the default account ID for the logged-in user on the OMS. |
| InstrumentId | **long integer.** The ID of the instrument being quoted. *Required*. |
| Bid          | **real.** The bid price. *Required*.                         |
| BidQty       | **real.** The quantity of the bid. *Required*.               |
| Ask          | **real.** The ask price. *Required*.                         |
| AskQty       | **real.** The quantity of the ask. *Required*.               |

### Response

```json
{
  "BidResult": {
    "result": true,
    "errormsg": "",
    "errorcode": 0,
    "detail": "",
  },
  "AskResult": {
    "result": true,
    "errormsg": "",
    "errorcode": 0,
    "detail": "",
  }
}
```

| Key       | Value                                                      |
| --------- | ---------------------------------------------------------- |
| BidResult | **object.** Returns a response object for Bid (see below). |
| AskResult | **object.** Returns a response object for Ask.             |

Objects for both *BidResult* and *AskResult*:

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean.** A successful receipt of the cancelation returns *true*; and unsuccessful receipt of the cancelation (an error condition) returns *false*. |
| errormsg  | **string.** A successful receipt of the cancelation returns *null*; the *errormsg* parameter for an unsuccessful receipt returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer.** A successful receipt of the cancelation returns 0. An unsuccessful receipt returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send. Usually null. |




