## SetAccountConfig

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Sets a single key-value configuration pair for the specified account. The Order Management System is assumed.

A user with Trading permission can set a key-value configuration pair only for the account with which the user is associated; a user with Operator permission can set a key-value pair for any account.

### Request

```json
{
    "accountId": 0,
    "accountHandle": "",
    "config": {"key": "keyname", "value": "keyValue"}
}
```

| Key           | Value                                                       |
| ------------- | ----------------------------------------------------------- |
| accountId     | **integer.** The ID of the account whose pair is being set. |
| accountHandle | **string.** A user-assigned name for the account.           |
| config        | **string.** The string value for *config* can be used to set any key-value config pair.   |

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


