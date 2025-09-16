## RevokeUserPermission

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Revokes the specified permission from the specified user.

The AlphaPoint Exchange offers several hundred possible permissions that can be granted to a user. The default permissions are:<br />Deposit<br />Trading<br />Withdraw

To see a list of available permissions on the Exchange, use **GetAvailablePermissionList.** To see a list of permissions already granted a specific user, use **GetUserPermissions.**

### Request

```json
{
    "UserId": 1,
    "Permission": "Trading"
}
```

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| UserId     | **integer.** The ID of the user whose permission you wish to revoke. |
| Permission | **string.** The name of the permission you wish to revoke.   |

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


