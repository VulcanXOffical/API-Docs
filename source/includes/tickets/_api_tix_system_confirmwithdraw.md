## ConfirmWithdraw

**Category:** System<br />**Permissions:** Public<br />**Call Type:** Synchronous

Checks whether the user has clicked the confirmation link in an email. The email confirms whether the user issued the withdrawal request.

### Request

```json
{
    "UserId": 1,
    "VerifyCode": "Verify Code GUID"
}
```

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| UserId     | **integer.** The ID of the calling user.                     |
| VerifyCode | **string.** The globally unique identifier (GUID) that identifies a specific withdrawal. |

### Response

```json
{
    "result": true
}
```

| Key    | Value                                                        |
| ------ | ------------------------------------------------------------ |
| result | **Boolean.** Returns *true* if the user has clicked the link in the confirming email). Returns false if the withdrawal has not clicked the link. |


