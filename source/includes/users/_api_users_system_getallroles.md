## GetAllRoles

**Category:** System<br />**Permissions:** Superuser, Operator, Trading <br />**Call Type:** Synchronous

Gets all of the available roles in the system.

### Request

```json
{}
```
No payload for GetAllRoles

### Response

```json
[
	{
		"roleName":"Operator",
		"permissions":["GetProducts","GetUserConfig","SetUserConfig "]
	},
	{
		"roleName":"Operator2",
		"permissions":["GetActiveUserSessions","UpdateDepositTicket","CreateDepositTicket"]
	}
]
```
The Response is a list of Roles.

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| roleName   | **string.** Name of role |
| permissions  | **string.** Permissions assoicated with the role |