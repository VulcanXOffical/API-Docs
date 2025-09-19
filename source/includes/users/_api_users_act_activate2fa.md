## Activate2FA

**Category:** Activation<br />
**Permissions:** Public<br />
**Call Type:** Synchronous

### Request

```json
{
  "Code": "YourCode"
}
```

In HTTP

```http
{
  "Code":"YourCode"
}
```

Completes the second half of a two-factor authentication by sending the 2FA code while registering for the exchange.

| Key  | Value                                                              |
| ---- | ------------------------------------------------------------------ |
| Code | **string.** The alphanumeric code you received for authentication. |

### Response

```json
{
  "Activated": true,
  "Error": "ErrorMessage"
}
```

| Key       | Value                                                                   |
| --------- | ----------------------------------------------------------------------- |
| Activated | **Boolean.** _True_ if the activation code is accepted; _false_ if not. |
| Error     | **string.** Error message from the server.                              |
