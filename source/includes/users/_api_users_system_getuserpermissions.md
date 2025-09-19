## GetUserPermissions

**Category:** System<br />**Permissions:** Operator, Trading, AccountReadOnly<br />**Call Type:** Synchronous

Returns a list of permissions for the specified user.

An Exchange offers a set of several hundred possible permissions that can be granted to a user. The default permissions are:<br />Deposit<br />Trading<br />Withdraw

To see a list of available permissions on the Exchange, use **GetAvailablePermissionList.** 

Users with Trading or AccountReadOnly permission can return a list of permissions only for a user associated with their default account; a user with Operator permission can return a list of permissions granted to any user.

### Request

```json
{
    "UserId": 1
}
```

| Key    | Value                                                        |
| ------ | ------------------------------------------------------------ |
| UserId | **integer.** The ID of the user whose permission set you want to return. |

### Response

```json
[
  "trading", "deposit", "withdraw"...]
]
```
The Response returns a list of all the permissions that pertain to the *UserId* provided in the Request.



