## AddUserMarketDataPermission

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Grants market data permission to a single user for a single instrument.

There are four types of market data: *Level 1,* *Level 2,* *Ticker,* and *Trades.* If a user has market data permission &mdash; granted here by **AddUserMarketDataPermission** &mdash; that user can subscribe to *Level1,* *Ticker,* and *Trades.* However, *Level 2* requires special permission, which is determined by the *level2* Boolean in the Request.

<aside class="notice"><strong>Note:</strong> The calls <strong>SubscribeLevel1,</strong> <strong>SubscribeLevel2,</strong> <strong>SubscribeTicker,</strong> and <strong>SubscribeTrades</strong> all require appropriate market data permissions issued by this call.</aside>

### Request

```json
{
    "userId": 0,
    "omsId": 0,
    "instrumentId": 0,
    "level2": false
}
```

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| userId       | **integer.** The ID of the user who is granted market data permission. |
| omsId        | **integer.** The ID of the Order Management System on which the user operates. |
| instrumentId | **integer.** The instrument whose market data the user is permitted to view. |
| level2       | **Boolean.** If the value of *level2* is *true,* the user can view Level 2 information about the instrument specified by *instrumentId* (including Ticker and Trade information). If the value of *level2* is *false,* the user can view only Level 1 information about the instrument (including Ticker and Trades) specified by *instrumentId.* |

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




