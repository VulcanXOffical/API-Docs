## GetUserGroupPermissions

**Category:** User<br />**Permissions:** SUPERUSER<br />**Call Type:** Synchronous

Retrieves an array of user group names and their permissions. See also: **SetUserGroupPermissions.**

### Request

```json
{ }
```

The request payload is empty.

### Response

```json
[
    {
        "UserGroupName":"",
        "PermissionName":""
    },
]
```

The response returns an array of user group names and their permission names.

| Key            | Value                                               |
| -------------- | --------------------------------------------------- |
| UserGroupName  | **string.** The name of a user group.               |
| PermissionName | **string.** A permission granted to the user group. |


