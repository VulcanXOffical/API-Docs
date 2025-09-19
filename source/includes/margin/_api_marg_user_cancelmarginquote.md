## CancelMarginQuote

**Category:** User<br />**Permissions:** Operator, Trading<br />**Call Type:** Asynchronous

Cancels a single margin quote.

A user with Trading permission can cancel quotes only for accounts he is associated with, and for products that that account can trade; a user with Operator permission can cancel quotes for any account and product.

<aside class="notice"><strong>Note: </strong>This is an asynchronous call.</aside>

### Request

```json
{
    "OMSId": 0,
    "ProductId": 0,
    "AccountId": 0,
    "ClientMarginQuoteId": 0,
    "MarginQuoteId": 0,
    "EnteredBy": 0
}
```

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| OMSId               | **integer.** The ID of the Order Management System on which the quote was made. |
| ProductId           | **integer.** The ID of the product that was quoted.          |
| AccountId           | **integer.** The ID of the account that made the quote.      |
| ClientMarginQuoteId | **long integer.** The ID of the client's margin quote ID (much like a purchase order number) assigned by the client. |
| MarginQuoteId       | **long integer.** The ID of the the margin quote assigned by the OMS.  |
| EnteredBy           | **integer.** The user ID of the person making the quote.     |

### Response

The server provides no response.
