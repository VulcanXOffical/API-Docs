## EnableXP2FA

**Category:** User<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

EnableXP2FA is a custom two-factor-authentication scheme (like Google 2FA). It generates 2FA code and has the ability to verify these codes.

### Request

```json
{
  "Phone": "",
  "Capability":""
}
```

| Key        | Value             |
| ---------- | ----------------- |
| Phone      | **string.** A 13-digit Brazilian phone number. Example: +5511965536992 |
| Capability | **string.** Method of validation. Possible values are:<br />SMS<br />Phone<br />OTP (an app) |

### Response

```json
{
  "Enabled2FA": true,
  "Activate2FA":true
}
```

| Key         | Value                                                        |
| ----------- | ------------------------------------------------------------ |
| Enabled2FA  | **Boolean.** *True* if XP two-factor authentication is enabled; *false* if not. |
| Activate2FA | **Boolean.** *True* if XP two-factor authentication is to be activated; *false* if not. |
