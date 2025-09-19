## SetDefaultOperatorOMS

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Sets the default Order Management System for a given operator.

To remove an operator from an Order Management System, use **RemoveOperatorOMS.**

### Request

```json
{
    "OperatorId": 1,
    "OMSId": 1,
    "IsDefault": true
}
```

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| OperatorId | **integer.** The ID of the operator you want to assign to the Order Management System. |
| OMSId      | **integer.** The ID of the Order Management System you want to assign to the Operator. |
| IsDefault  | **Boolean.** If the value is *true,* this is the default Order Management System for the operator. If *false,* it is not. |

### Response

```json
{
    "result": true,
    "errormsg": "",
    "errorcode": 0,
    "detail": ""
}
```
The Response is a standard response object.

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean.** If the call has been successfully received by the Order Management System, *result* is *true;* otherwise it is *false.* |
| errormsg  | **string.** A successful receipt of the call returns *null.* The *errormsg* key for an unsuccessful call returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer.** A successful receipt of the call returns 0. An unsuccessful receipt of the call returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send.           |
