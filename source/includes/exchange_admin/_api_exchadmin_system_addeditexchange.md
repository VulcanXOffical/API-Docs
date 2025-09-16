## AddEditExchange

**Category:** System<br />**Permissions:** SUPERUSER<br />**Call Type:** Synchronous

Adds a new logical Exchange to a running matching engine or updates an existing Exchange.

Only a SUPERUSER can create or update a new logical Exchange.

### Request

```json
{
    "exchangeServiceId": "V2ExchangeCore",
    "exchangeId": 0
}
```
The AlphaPoint Exchange "knows" if these key-value pairs already exist. If the values you provide don't currently exist, the system creates a new instance.

| Key               | Value                                                        |
| ----------------- | ------------------------------------------------------------ |
| exchangeServiceId | **string.** The name of the matching engine on which the new Exchange will be created. |
| exchangeId        | **integer.** Assign a value to a newly created exchange or changes the ID of an existing exchange.     |



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


