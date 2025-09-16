## GetTreasuryProductsForAccount

**Category:** User<br />**Permissions:** Operator, Trading, Withdraw, Deposit<br />**Call Type:** Synchronous

Returns a list of product symbols (BTC, USD, etc.) upon which the account named by AccountId is allowed to execute treasury operations.

Users with Trading, Withdraw, and Deposit permission must be associated with the account named by AccountId. Users with Operator permission can request the list of treasury products for any account.


### Request

```json
{
    "AccountId": 1,
    "OMSId": 1
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| AccountId | **integer.** The ID of the account whose permitted treasury products will be returned. |
| OMSId     | **integer.** The ID of the Order Management System where the account operates. |

### Response

> An array of code symbol lists.

```json
[ { "LTC", "BTC", "USD" }, ]
```

The response returns an array of code symbol lists.

