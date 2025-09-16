## GetRole

**Category:** System<br />**Permissions:** Operator, Trading <br />**Call Type:** Synchronous

Gets the specified role based on the role id passed in the payload.

### Request

```json
{
	"roleId": 1,
}
```

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| roleId       | **integer.** Id of role |


### Response

```json
{
	"roleName":"Operator",
	"permissions":["GetProducts","GetUserConfig","SetUserConfig "]
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| roleName   | **string.** Name of role |
| permissions  | **string.** Permissions assoicated with the role |