## AddUserPermission

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Grants a single permission to the specified user. There are several hundred highly specific permissions that you can grant a user. To see a list of available permissions, use **GetAvailablePermissionsList.**

### Request

```json
{
    "UserId": 1,
    "Permission": "Trading",
    "Value": 1
}
```

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| UserId     | **integer.** The ID of the user to whom you are adding the permission. |
| Permission | **string.** The name of the permission. There are hundreds of highly specific permissions that you can grant. The default permissions are:<br />Deposit<br />Trading<br />Withdraw |
| Value      | **integer.** The key-value pair *Value* is present for backwards compatibility with earlier versions of the Exchange, where the 0 value indicated *remove the permission.* For versions of the Exchange after v3.1, set this value to 1.    |

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
