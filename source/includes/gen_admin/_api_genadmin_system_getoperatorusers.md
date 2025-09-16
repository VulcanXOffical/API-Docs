## GetOperatorUsers (DEPRECATED)

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Returns a list of users who are associated with a specific operator.

In earlier versions of the AlphaPoint Exchange, users were associated with an operator. This is no longer the case. You should not use this call.

<aside class="warning"><strong>Note: This call is DEPRECATED.</strong></aside>

### Request

```json
{
    "OperatorId": 1
}
```

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| OperatorId | **integer.** The ID of the operator whose corresponding user IDs you want to return. |

### Response

```json
[
    {
        "operatorId": 0,
        "userId": 0
    }, 
]
```

The Response is an array of operator IDs and the user IDs associated with them.

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| operatorId | **integer.** The ID of the operator echoed back from the Request. |
| userId     | **integer.** The user ID associated with that operator ID.   |
