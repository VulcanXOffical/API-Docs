## GetLockedUsers

**Category:** System<br />**Permissions:** SUPERUSER, Operator, UserOperator<br />**Call Type:** Synchronous

Returns an array of locked users.

A user may be locked because of a rapid series of attempted logins.

Users with SUPERUSER or Operator permission can return a list of all locked users on the Exchange; users with UserOperator permissions can return locked user information only for their own accounts.

### Request

```json
{}
```

The Request for **GetLockedUsers** has no payload.

### Response

```json
[
    {
        "userId":0,
        "userName":"",
        "email":"",
        "lockedDateTime":"0001-01-01T00:00:00"
    },
]
```

| Key            | Value                                                        |
| -------------- | ------------------------------------------------------------ |
| userId         | **integer.** The ID of the user who is locked.               |
| userName       | **string.** The user name of the user who is locked (may not be the user's full name). |
| email          | **string.** The locked user's verified email address.        |
| lockedDateTime | **string.** The date and time that the user was locked, in Microsoft Ticks format and UTC time zone. |


