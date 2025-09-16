## GetProducts

**Category:** User<br />
**Permissions:** Public<br />
**Call Type:** Synchronous

Returns an array of products available on the exchange. A product is an asset that is tradable or paid out.

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

//Get all enabled products
await apex.RPCPromise('GetProducts',{
OMSId: 1,
})

//Get all products including disabled products
await apex.RPCPromise('GetProducts',{
OMSId: 1,
GetDisabled: true //or
GetDisabled: 1
})

//Get all products that matches an attribute and its value
await apex.RPCPromise('GetProducts',{
OMSId: 1,
Attribute: "Pegged"
AttributeValue: true
})

//Starting APEX version 4.4, Depth and StartIndex fields are already supported
await apex.RPCPromise('GetProducts',{
OMSId: 1,
GetDisabled: 1,
Depth: 10, //will only return max 10 results
StartIndex: 0, //will return products starting from Productd 1, a StartIndex of 10 will return products starting from ProductId 11(means that ProductsId 1 - 10 will not be in he results)
})
```

```http
POST /AP/GetProducts HTTP/1.1
Host: apialphapointuniversitystaging.cdnhop.net:8443
Content-Type: application/json
Content-Length: 20
//Get all enabled products
{
    "OMSId": 1
}
//Get all products including disabled products
{
    "OMSId": 1,
    "GetDisabled": true
}
//Get all products that matches an attribute and its value
{
    "OMSId": 1,
    "Attribute": "Pegged",
    "AttributeValue": true
}

//Starting APEX version 4.4 Depth and StartIndex fields are already supported
{
  "OMSId": 1,
  "GetDisabled": 1,
  "Depth": 10, //will only return max 10 results
  "StartIndex": 0, //will return products starting from Productd 1, a StartIndex of 10 will return products starting from ProductId 11(means that ProductsId 1 - 10 will not be in he results)
}
```

| Key            | Value                                                                                                                                                      |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| OMSId          | **integer.** The ID of the Order Management System for which the array of available products will be returned._required._                                  |
| Attribute      | **string.** The attribute key or name for which you want to filter the results with._optional._                                                            |
| AttributeValue | **string.** Used to filter the results further, only products whose attribute value will match the one set will be returned._optional_                     |
| GetDisabled    | **bool or integer.** Used to filter disabled products, setting this to true will return all products including the disabled ones._optional_                |
| Depth          | **integer.** Used for pagination. Indicates the maximum number of results to be returned._optional_                                                        |
| StartIndex     | **integer.** Used for pagination. ProductId 1 represents index 0. A value of 2 for this field will not include ProductId 1 and 2 in the results._optional_ |

### Response

```javascript
[
  {
    OMSId: 1,
    ProductId: 1,
    Product: "USD",
    ProductFullName: "US Dollar",
    MasterDataUniqueProductSymbol: "",
    ProductType: "NationalCurrency",
    DecimalPlaces: 2,
    TickSize: 0.01,
    DepositEnabled: true,
    WithdrawEnabled: true,
    NoFees: false,
    IsDisabled: false,
    MarginEnabled: false,
  },
  {
    OMSId: 1,
    ProductId: 2,
    Product: "BTC",
    ProductFullName: "Bitcoin",
    MasterDataUniqueProductSymbol: "",
    ProductType: "CryptoCurrency",
    DecimalPlaces: 8,
    TickSize: 0.00000001,
    DepositEnabled: true,
    WithdrawEnabled: true,
    NoFees: false,
    IsDisabled: false,
    MarginEnabled: false,
  },
];
```

```http
[
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
    },
    {
        "OMSId": 1,
        "ProductId": 2,
        "Product": "BTC",
        "ProductFullName": "Bitcoin",
        "MasterDataUniqueProductSymbol": "",
        "ProductType": "CryptoCurrency",
        "DecimalPlaces": 8,
        "TickSize": 0.0000000100000000000000000000,
        "DepositEnabled": true,
        "WithdrawEnabled": true,
        "NoFees": false,
        "IsDisabled": false,
        "MarginEnabled": false
    }
]
```

The response returns an array of objects, one object for each product available on the Order Management System.

| Key             | Value                                                                                                                                                                                                                                                                 |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| OMSId           | **integer.** The ID of the Order Management System that offers the product.                                                                                                                                                                                           |
| ProductId       | **long integer.** The ID of the product.                                                                                                                                                                                                                              |
| Product         | **string.** “Nickname” or shortened name of the product. For example, NZD (New Zealand Dollar).                                                                                                                                                                       |
| ProductFullName | **string.** Full and official name of the product. For example, New Zealand Dollar.                                                                                                                                                                                   |
| ProductType     | **integer.** A number describing the nature of the product. One of:<br />0 Unknown (an error condition)<br />1 NationalCurrency<br />2 CryptoCurrency<br />3 Contract                                                                                                 |
| DecimalPlaces   | **integer.** The number of decimal places in which the product is divided. The maximum is 8. For example, US Dollars are divided into 100 units, or 2 decimal places. Other products may be different. Burundi Francs use 0 decimal places and the Rial Omani uses 3. |
| TickSize        | **real.** The smallest increment in which the product can trade.                                                                                                                                                                                                      |
| NoFees          | **Boolean.** Shows whether trading the product incurs transaction fees. The default is _false_; that is, if _NoFees_ is _false_, transaction fees will be incurred. If _NoFees_ is _true_, no fees are incurred.                                                      |
