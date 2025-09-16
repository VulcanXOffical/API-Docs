## GetProduct

**Category:** Trading<br />
**Permissions:** Public<br />
**Call Type:** Synchronous

Retrieves the details about a specific product on the exchange. A product is an asset that can be deposited and withdrawn but cannot be traded, an instrument is the one that can be traded.

### Request

```javascript
const { APEX } = require("VulcanX-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("GetProduct", {
  OMSId: 1,
  ProductId: 1,
});
```

```http
POST /AP/GetProduct HTTP/1.1
Host: hostname goes here...
Content-Type: application/json
Content-Length: 41

{
    "OMSId": 1,
    "ProductId": 1
}
```

| Key       | Value                                                                                        |
| --------- | -------------------------------------------------------------------------------------------- |
| OMSId     | **integer.** The ID of the Order Management System that includes the product._required._     |
| ProductId | **long integer.** The ID of the product on the specified Order Management System._required._ |

### Response

Returns an object with fields named as to what they mean.

```javascript
{
    "OMSId": 1,
    "ProductId": 1,
    "Product": "USD",
    "ProductFullName": "US Dollar",
    "MasterDataUniqueProductSymbol": "",
    "ProductType": "NationalCurrency",
    "DecimalPlaces": 2,
    "TickSize": 0.0100000000000000000000000000,
    "DepositEnabled": true,
    "WithdrawEnabled": true,
    "NoFees": false,
    "IsDisabled": false,
    "MarginEnabled": false
}
```

```http
{
    "OMSId": 1,
    "ProductId": 1,
    "Product": "USD",
    "ProductFullName": "US Dollar",
    "MasterDataUniqueProductSymbol": "",
    "ProductType": "NationalCurrency",
    "DecimalPlaces": 2,
    "TickSize": 0.0100000000000000000000000000,
    "DepositEnabled": true,
    "WithdrawEnabled": true,
    "NoFees": false,
    "IsDisabled": false,
    "MarginEnabled": false
}
```

| Key             | Value                                                                                                                                                                                                                                                                 |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| OMSId           | **integer.** The ID of the Order Management System that offers the product.                                                                                                                                                                                           |
| ProductId       | **long integer.** The ID of the product.                                                                                                                                                                                                                              |
| Product         | **string.** “Nickname” or shortened name of the product. For example, NZD (New Zealand Dollar).                                                                                                                                                                       |
| ProductFullName | **string.** Full and official name of the product. For example, New Zealand Dollar.                                                                                                                                                                                   |
| ProductType     | **string.** The nature of the product. One of:<br />0 Unknown (an error condition)<br />1 NationalCurrency<br />2 CryptoCurrency<br />3 Contract                                                                                                                      |
| DecimalPlaces   | **integer.** The number of decimal places in which the product is divided. The maximum is 8. For example, US Dollars are divided into 100 units, or 2 decimal places. Other products may be different. Burundi Francs use 0 decimal places and the Rial Omani uses 3. |
| TickSize        | **real.** The smallest increment in which the product may trade.                                                                                                                                                                                                      |
| NoFees          | **Boolean.** Shows whether trading the product incurs transaction fees. The default is _false_; that is, if _NoFees_ is _false_, transaction fees will be incurred. If _NoFees_ is _true_, no fees are incurred.                                                      |
