## CreateOperatorLoyaltyFeeConfig

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Creates a new operator loyalty configuration for discounted transactions involving a specified product (token).

An exchange can promote activity in a specific cryptocurrency token by offering discounted transaction fees denominated in the token to customers who accept this fee structure. The Loyalty Token is a parallel fee structure that replaces the general set of transaction fees.

You can set one Loyalty Token per Order Management System. An OMS is not required to offer a Loyalty Token or fee.

Delete an existing operator loyalty fee configuration using **DeleteOperatorLoyaltyFeeConfig.**

### Request

```json
{
    "omsId": 0,
    "loyaltyProductId": 0,
    "loyaltyDiscount": 0.0,
    "referenceProductId": 0,
    "referenceProductPrice": 0.0,
    "isEnabled": true,
    "lastUpdated": "0001-01-01T00:00:00",
    "updatedBy": 0
}
```

| Key                  | Value                                                        |
| -------------------- | ------------------------------------------------------------ |
| omsId                | **integer.** The ID of the Order Management System where you want to offer the Loyalty Token. |
| loyaltyProductId     | **integer.** The ID of the loyalty product, a cryptocurrency. |
| loyaltyDiscount      | **real.** The discount from the standard transaction fee that you are willing to apply. For example, 0.5 (denominated in the loyalty product); a value of 0.5 equals 50%. |
| referenceProductId   | **integer.** The ID of the default base currency to use to calculate the exchange rate between regular fee products and the discount product. Basis is the last trade price of the product pairing, for example, loyalty product/reference product. See the note below for **Reference Product Example.** |
| refereceProductPrice | **real.** The default market value (see **Reference Product Example,** below) of a product expressed in a default base currency to use in the event there is no "last traded price" for the XYZ/Reference_product market. This value is applicable only if there is no XYZUSD market on the Exchange (see example). |
| isEnabled            | **Boolean.** When *true,* allows transactions to use the Loyalty Token and Fee. |
| lastUpdated          | **string.** The date and time when the loyalty configuration was last updated, expressed in Microsoft Ticks format and UTC time zone. |
| updatedBy            | **integer.** The ID of the operator who made the most recent configuration change. |

**Reference Product Example** &mdash; An exchange lists BTCGBP, BITCUSD, ETHBTC, XYZUSD, and XYZGBP. If the regular fee product is BTC on a trade, and you want to give a discount to XYZ, you must convert BTC to XYZ through a default currency because there is no direct BTCXYZ instrument. The Exchange can convert the BTC to XYZ via the default base currency of the instruments of the Exchange, the *referenceProductId.*

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

