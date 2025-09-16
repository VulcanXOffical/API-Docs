## Validate2FA

**Category:** System<br />**Permissions:** <br />**Call Type:** Synchronous

Validate 2FA to get access to the 2FA required endpoints

### Request

```json
{
	"TFaType":"TFATYPE",
	"Code": "YourCode"
}
```

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| TFaType     | **string.** Type of authentication |
| Code     | **string.** Authentication code |

### Response

```json
{
	"TFaAuthenticated": true
}
```

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| TFaAuthenticated     | **Boolean.**  If authenticatation is successful, returns true|