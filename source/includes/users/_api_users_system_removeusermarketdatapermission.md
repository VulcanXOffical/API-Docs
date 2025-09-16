## RemoveUserMarketDataPermission

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Removes all levels of market data permission from a user for the specified instrument.

There are four types of market data: *Level 1,* *Level 2,* *Ticker,* and *Trades.* This call removes *all levels of market data permission* for the specified instrument, regardless of the value of the *level2* Boolean, which is simply part of the object that describes a user's permissions for an instrument.

See **AddUserMarketDataPermission** for information about adding permissions and **GetUserMarketDataPermissions** for a list of permissions that pertain to a single user.

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
| userId       | **integer.** The ID of the user whose market data permission you want to remove. |
| omsId        | **integer.** The ID of the Order Management System on which the user operates. |
| instrumentId | **integer.** The ID of the instrument whose market information permission you want to remove. |
| level2       | **Boolean.** Generally, a *true* or *false* value for *level2* determines whether a user can view Level 2 market data. However, **RemoveUserMarketDataPermission** removes all levels of user market data permission (including Ticker and Trades). The value of *level2* in this instance is ignored. |

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
