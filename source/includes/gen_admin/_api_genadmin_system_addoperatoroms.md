## AddOperatorOMS

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Assigns an existing Order Management System to an existing user who already has Operator permission.

### Request

```json
{
    "operatorId": 0,
    "omsId": 0,
    "isDefault": false
}
```

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| operatorId | **integer.** The ID of the operator to whom you will assign the Order Management System. |
| omsId      | **integer.** The ID of the Order Management System you will assign to the operator. |
| isDefault  | **Boolean.** If *true,* this Order Management System is the default OMS for this operator; if *false,* it is not. An operator can be assigned one default Order Management System. |

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


