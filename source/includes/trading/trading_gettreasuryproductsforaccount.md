## GetTreasuryProductsForAccount

**Category:** Trading<br />
**Permissions:** Operator, Trading, Withdraw, Deposit<br />
**Call Type:** Synchronous

Returns a list of products upon which the account id is allowed to execute treasury operations. Technically, the products returned are those products with a configured and enabled **AccountProvider**.

Users with Trading, Withdraw, and Deposit permissions can call this API only for the accounts associated to them. Users with Operator permission can request the list of treasury products for any account.

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("GetTreasuryProductsForAccount", {
  AccountId: 1,
  OMSId: 1,
});
```

```http
POST /AP/GetTreasuryProductsForAccount HTTP/1.1
Host: hostname goes here...
aptoken: b031b607-818d-4799-9f5f-b07c7a28dd58 //valid sessiontoken
Content-Type: application/json
Content-Length: 41

{
    "OMSId": 1,
    "AccountId": 7
}
```

| Key       | Value                                                                                             |
| --------- | ------------------------------------------------------------------------------------------------- |
| AccountId | **integer.** The ID of the account whose permitted treasury products will be returned._required._ |
| OMSId     | **integer.** The ID of the Order Management System where the account operates._required._         |

### Response

> An array of product symbols, each element of the array corresponds to a product.

```javascript
[
  "ETH",
  "LINK",
  "USD",
  "ICX",
  "BTC",
  "USD",
  "TXRP",
  "ETH",
  "APU",
  "OTC",
  "test2",
  "BTC",
];
```

```http
[
  "ETH",
  "LINK",
  "USD",
  "ICX",
  "BTC",
  "USD",
  "TXRP",
  "ETH",
  "APU",
  "OTC",
  "test2",
  "BTC",
];
```
