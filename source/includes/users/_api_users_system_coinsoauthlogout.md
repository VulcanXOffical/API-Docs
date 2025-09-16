## CoinsOAuthLogout

**Category:** System<br />**Permissions:** Public<br />**Call Type:** Synchronous

Logs a user off the Exchange using the *OAuth* protocol.

### Request

```json
{}
```

The Request has no payload.

### Response

```json
{
    "CoinsOAuthLogout": true,
    "User": ""
}
```

| Key              | Value                                                        |
| ---------------- | ------------------------------------------------------------ |
| CoinsOAuthLogout | **Boolean.** If the value is *true,* the user successfully has been logged out. If the value is *false,* the user has not successfully been logged out. |
| User             | **string.** The user name of the user being logged out.      |


