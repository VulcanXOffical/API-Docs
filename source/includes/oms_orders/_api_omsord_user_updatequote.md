## UpdateQuote

**Category:** User<br />
**Permissions:** Operator, MarketMaker<br />
**Call Type:** Synchronous

Updates an existing quote. Quoting is not enabled for the retail end user of the AlphaPoint software. Only registered market participants or market makers may quote.

<aside class="warning"><strong>Warning</strong> **UpdateQuote** resets the quote's priority in the order book.</aside>

### Request

```json
{
	"OMSId": 0,
	"AccountId": 0,
	"InstrumentId": 0,
	"BidQuoteId": 0,
	"Bid": 0,
	"BidQTY": 0,
	"AskQuoteId": 0,
	"Ask": 0,
	"AskQTY": 0,
}
```

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| OMSId        | **integer.** The ID of the Order Management System where the quote is located. |
| AccountId    | **integer.** The ID of the account whose quote will be updated. |
| InstrumentId | **long integer.** The ID of the instrument whose quote is being updated. |
| BidQuoteId   | **integer.** The ID of the original bid quote being updated. |
| Bid          | **real.** The new amount of the bid quote.                   |
| BidQTY       | **real.** The new quantity of the bid quote.                 |
| AskQuoteId   | **integer.** The ID of the original ask quote being updated. |
| Ask          | **real.** The new amount of the ask quote.                   |
| AskQTY       | **real.** The new quantity of the ask quote.                 |

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
| result    | **Boolean.** A successful receipt of the update returns *true*; and unsuccessful receipt of the update (an error condition) returns *false*. |
| errormsg  | **string.** A successful receipt of the update returns *null*; the *errormsg* parameter for an unsuccessful receipt returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer.** A successful receipt of the update returns 0. An unsuccessful receipt returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send. Usually null. |



