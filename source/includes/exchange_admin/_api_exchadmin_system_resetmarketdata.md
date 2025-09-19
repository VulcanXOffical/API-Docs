## ResetMarketData

**Category:** System<br />**Permissions:** SUPERUSER<br />**Call Type:** Synchronous

Resets market data for a specific instrument and Order Management System. Only a user with SUPERUSER permission can issue **ResetMarketData.**

**Implications:** Resetting market data for an instrument:

- Cleans and resets market data.
- Resets (cancels) all subscriptions, clears the cache, and starts over.
- Cancels all orders for the instrument.

### Request

```json
{
    "omsId": 0,
    "instrumentId": 0
}
```

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| omsId        | **integer.** The ID of the Order Management System that holds the instrument market you want to reset. |
| instrumentId | **integer.** The ID of the instrument whose market you want to reset. |



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
