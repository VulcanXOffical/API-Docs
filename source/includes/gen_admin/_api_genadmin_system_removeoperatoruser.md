## RemoveOperatorUser (DEPRECATED)

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Removes a single user from association with a given operator.

In earlier versions of the AlphaPoint Exchange, users were associated with an operator. This is no longer the case. You should not use this call.

<aside class="warning"><strong>Note: This call is DEPRECATED.</strong></aside>

### Request

```json
{
    "operatorId": 0,
    "userId": 0
}
```

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| operatorId | **integer.** The ID of the operator whose user you want to remove. |
| userId     | **integer.** The ID of the user you want to disassociate from the operator. |

### Response

```json
{
    "Success": true
}
```

| Key     | Value                                                        |
| ------- | ------------------------------------------------------------ |
| Success | **Boolean.** If *true,* the user has been successfully removed. If *false,* the user has not been successfully removed. |


