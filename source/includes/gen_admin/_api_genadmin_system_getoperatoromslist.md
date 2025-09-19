## GetOperatorOMSList

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Returns an array of Order Management Systems that a given operator can manage.

### Request

```json
{
    "OperatorId": 1
}
```

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| OperatorId | **integer.** The ID of the operator whose Order Management Systems you want to return. |

### Response

```json
[
    {
        "OperatorId": 1,
        "OMSId": 1,
        "IsDefault": true
    },
]
```

The Response is an array of the Order Management Systems which an operator can manage.

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| OperatorId | **integer.** The ID of the operator.                         |
| OMSId      | **integer.** The ID of the Order Management System.          |
| IsDefault  | **Boolean.** If the value is *true,* this is the default Order Management System that the operator manages; if the value is *false,* the OMS is not the default. An operator can have one default Order Management System. |




