## GetAllUserGroupPermissions

**Category:** User<br />**Permissions:** SUPERUSER<br />**Call Type:** Synchronous

Retrieves all user group permissions.

### Request

```json
{}
```

No payload in the request.

### Response

```json
[
    {
        "UserGroupName":"",
        "PermissionName":""
    },
]
```

The response returns an array of user group names and permissions that apply to the user group.

| Key            | Value                                                        |
| -------------- | ------------------------------------------------------------ |
| UserGroupName  | **string.** The name of the user group.                      |
| PermissionName | **string.** The name of the permission that has been granted to the members of the user group. |


