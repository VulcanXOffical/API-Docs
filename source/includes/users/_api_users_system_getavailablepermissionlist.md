## GetAvailablePermissionList

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Returns a list of all possible user permissions. There are over 300 possible permissions.

The call **AddUserPermission** adds a specified permission to a specified user. The call **GetUserPermissions** returns the permissions already assigned to a specified user. The call **RevokeUserPermission** removes a specified permission from a specified user.

### Request
>The Request requires no payload.

```json
{}
```

The Request requires no payload.

### Response

```json
{
    "permissionList": "AdminUI", "UserOperator", "AccountOperator", "AccountReadOnly", "GetAvailablePermissionList", ...
}
```

The Response returns a KVP named *permissionList,* whose value is a comma-separated list of strings naming the permissions available to assign to users on the system.


