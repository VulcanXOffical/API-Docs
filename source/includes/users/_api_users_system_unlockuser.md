## UnLockUser

**Category:** System<br />**Permissions:** SUPERUSER, Operator, UserOperator<br />**Call Type:** Synchronous

Unlocks a locked user. A user may be locked by attempting to login rapidly too many times. A locked user cannot log in. An admin must unlock the locked user.

Users with UserOperator permission can unlock themselves. Users with SUPERUSER or Operator permission can unlock any user.

### Request

```json
{
    "UserId": 1
}
```

| Key    | Value                                               |
| ------ | --------------------------------------------------- |
| UserId | **integer.** The ID of the user you want to unlock. |

### Response

```json
{
    true
}
```

If the user is successfully unlocked, the Response is a single Boolean *true*. If the user is not unlocked, the Response is a Boolean *false.*


