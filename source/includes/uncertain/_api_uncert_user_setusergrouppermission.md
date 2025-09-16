## SetUserGroupPermission

**Category:** User<br />**Permissions:** SUPERUSER<br />**Call Type:** Synchronous

Creates a user group permission mapping; that is, it creates the key-value pair that represents a permission granted to a user group. The user group and the permission must already exist.

### Request

```json
{
    "UserGroupName":"",
    "PermissionName":""
}
```

| Key            | Value                                                        |
| -------------- | ------------------------------------------------------------ |
| UserGroupName  | **string.** The name of the user group whose permission is being set. |
| PermissionName | **string.** The name of the permission.                      |

### Response

```json
{
    "result":true,
    "errormsg":"",
    "errorcode":0,
    "detail":""
}
```

A successful response means that the server has received the request from **SetUserGroupPermissions,** not that the permission has been set. To find out if the permission has been set, use **GetUserGroupPermissions.**

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean**. A successful response returns *true*; an unsuccessful response (an error condition) returns *false*. |
| errormsg  | **string**. A successful response returns *null*; the *errormsg*  parameter for an unsuccessful receipt returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104) |
| errorcode | **integer**. A successful receipt returns *0*. An unsuccessful receipt returns one of the errorcodes shown in the *errormsg*list. |
| detail    | **string**. Message text that the system may send. Usually *null*. |
