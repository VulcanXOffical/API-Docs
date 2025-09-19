## GetOperatorLoyaltyFeeConfig

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Retrieves configuration information for a specified operator loyalty fee configuration on a single given Order Management System.

An exchange can promote activity in a specific cryptocurrency token by offering discounted transaction fees denominated in the token to customers who accept this fee structure. The Loyalty Token is a parallel fee structure that replaces the general set of transaction fees.

Users with Trading permission can get operator loyalty fee configurations that affect accounts with which they're associated; users with Operator permission can get anyoperator loyalty fee configurations.

### Request

```json
{
    "omsId": 0,
    "loyaltyProductId": 0
}
```
| Key                  | Value                                                        |
| -------------------- | ------------------------------------------------------------ |
| omsId                | **integer.** The ID of the Order Management System.          |
| loyaltyProductId     | **integer.** The ID of the loyalty product, a cryptocurrency. |

### Response

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
The Response is an array of loyalty fee configurations.

| Key                  | Value                                                        |
| -------------------- | ------------------------------------------------------------ |
| omsId                | **integer.** The ID of the Order Management System where the Loyalty Token is available. |
| loyaltyProductId     | **integer.** The ID of the loyalty product, a cryptocurrency. |
| loyaltyDiscount      | **real.** The discount from the standard transaction fee that you are willing to apply. For example, 0.5 (denominated in the loyalty product); a value of 0.5 equals 50%. |
| referenceProductId   | **integer.** The ID of the default base currency to use to calculate the exchange rate between regular fee products and the discount product. Basis is the last trade price of the product pairing, for example, loyalty product/reference product. See the note below for **Reference Product Example.** |
| refereceProductPrice | **real.** The default market value (see **Reference Product Example,** below) of a product expressed in a default base currency to use in the event there is no "last traded price" for the XYZ/Reference_product market. This value is applicable only if there is no XYZUSD market on the Exchange (see example). |
| isEnabled            | **Boolean.** When *true,* allows transactions to use the Loyalty Token and Fee. |
| lastUpdated          | **string.** The date and time when the loyalty configuration was last updated, expressed in Microsoft Ticks format and UTC time zone. |
| updatedBy            | **integer.** The ID of the operator who made the most recent configuration change. |

**Reference Product Example** &mdash; An exchange lists BTCGBP, BITCUSD, ETHBTC, XYZUSD, and XYZGBP. If the regular fee product is BTC on a trade, and you want to give a discount to XYZ, you must convert BTC to XYZ through a default currency because there is no direct BTCXYZ instrument. The Exchange can convert the BTC to XYZ via the default base currency of the instruments of the Exchange, the *referenceProductId.*
