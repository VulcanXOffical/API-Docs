## GetValidate2FARequiredEndpoints

**Category:** System<br />**Permissions:** Public<br />**Call Type:** Synchronous

Gets endpoints that require 2FA Validation
### Request

```json
{}
```

There is no payload.

### Response

```json
["createwithdrawticket", "createdepositticket", "adduserpermission"]
```
The response is a list of endpoints, all lowercase.

