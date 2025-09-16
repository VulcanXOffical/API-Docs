## GetUserMarketDataPermissions

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Retrieves a list of permissions that a single user has been granted for viewing market data about one or more instruments.

There are four types of market data: *Level 1,* *Level 2,* *Ticker,* and *Trades.* If a user has market data permission, that user can subscribe to *Level1,* *Ticker,* and *Trades.* However, *Level 2* requires special permission, which is determined by the value of the *level2* Boolean in the Response.

To add a market data permission, use **AddUserMarketDataPermission.** To remove a market data permission, use **RemoveUserMarketDataPermission.** Only a user with Operator permission can add or remove a market data permission.

Users with Trading permission can retrieve market data permissions only for users associated with their default account; users with Operator permission can retrieve market data permissions for any user.

<aside class="notice"><strong>Note:</strong> The calls <strong>SubscribeLevel1,</strong> <strong>SubscribeLevel2,</strong> <strong>SubscribeTicker,</strong> and <strong>SubscribeTrades</strong> all require appropriate market data permissions.</aside>

### Request

```json
{
    "UserId": 1
}
```

| Key    | Value                                                        |
| ------ | ------------------------------------------------------------ |
| UserId | **integer.** The ID of the user whose market data permissions you want to return. |

### Response

```json
[
    {
        "userId": 0,
        "omsId": 0,
        "instrumentId": 0,
        "level2": false
    }
]
```

The Response returns an array of information instrument-by-instrument.

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| userId       | **integer.** The ID of the user granted this market data permission. |
| omsId        | **integer.** The ID of the Order Management System on which the user operates. |
| instrumentId | **integer.** The ID of the instrument whose market data the user is permitted to view. |
| level2       | **Boolean.** If the value of *level2* is *true,* the user can view Level 2 information about the instrument specified by *instrumentId* (including Ticker and Trade information). If the value of *level2* is *false,* the user can view only Level 1 information about the instrument (including Ticker and Trades). |


