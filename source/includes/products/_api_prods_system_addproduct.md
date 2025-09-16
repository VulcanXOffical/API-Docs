## AddProduct

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Creates a new product definition on a given Order Management System.

### Request

```json
{
    "OMSId": 1,
    "ProductId": 26,
    "DecimalPlaces": 2,
    "Product": "ABC",
    "ProductFullName": "ABCs",
    "ProductType": 0,
    "TickSize": 0.0,
    "NoFees": true
}
```

| Key             | Value                                                        |
| --------------- | ------------------------------------------------------------ |
| OMSId           | **integer.** The ID of the Order Management System to which you are adding the product. |
| ProductId       | **integer.** The ID of the product on the Order Management System. You can set this to 0 when adding a new product, or you can define a product ID by putting a number in this value. Any product ID you assign **must** be unique across the Exchange, so it's best to allow the system to do it for you. The system assigns the ID; the Response returns that value as *Id*. |
| DecimalPlaces   | **integer.** The number of decimal places in which the product can be denominated. For example, US Dollars have two decimal places (you can have $0.01 of a dollar). |
| Product         | **string.** The trading symbol of the product. For example, BTC. |
| ProductFullName | **string.** The full name of the product. For example, BitCoin. |
| ProductType     | **integer.** The nature of the product. One of:<br />**0** Unknown (an error condition)<br />**1** NationalCurrency (fiat currency)<br />**2** CryptoCurrency<br />**3** Contract |
| TickSize        | **real.** The smallest increment in which the product may trade. This is not the same as the number of decimal places in which the product is denominated. For example, you may have a product denominated to two decimal places (10.05) but whose *TickSize* is 1. |
| NoFees          | **Boolean.** Shows whether trading the product incurs transaction fees. The default is *false,* that is, if *NoFees* is *false,* transaction fees will be incurred. If *NoFees* is *true,* no fees are incurred. |

### Response

```json
{
    "Id": 26,
    "RejectMessage":""
}
```

| Key           | Value                                                        |
| ------------- | ------------------------------------------------------------ |
| Id            | **integer.** The ID of the recently added product, The value of *productId.* |
| RejectMessage | **string.** If the addition of the new product is rejected by the system, the value of this key holds a human-readable reason for the rejection. If the new product has been accepted by the system, this value is empty. |


