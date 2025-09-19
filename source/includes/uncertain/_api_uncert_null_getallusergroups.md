## GetAllUserGroups

**Category:** Null<br />**Permissions:** SUPERUSER<br />**Call Type:** Synchronous

Retrieves an array of all names of user groups and their associated permissions. 

### Request

```json
{ }
```

Payload is empty.

### Response

```json
[
    {
        "UserGroupName":"",
        "PermissionName":""
    },
]
```

The response returns an array of user group names and their permissions.

| Key            | Value                                                        |
| -------------- | ------------------------------------------------------------ |
| UserGroupName  | **string.** The name of a user group.                        |
| PermissionName | **string.** The name of a permission associated with the group. |


