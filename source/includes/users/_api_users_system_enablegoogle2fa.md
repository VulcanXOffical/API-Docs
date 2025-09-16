## EnableGoogle2FA

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Enables Google two-factor authentication for a user's login. Both users with Trading permission and users with Operator permission can enable Google2FA only for their own accounts.

### Request

```json
{}
```

No payload.

### Response

```json
{
    "GoogleQRCode": "QR Code"
}
```

| Key          | Value       |
| ------------ | ----------- |
| GoogleQRCode | **string.** A string value describing the QR code. |


