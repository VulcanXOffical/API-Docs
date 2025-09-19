## ResubmitFailedWithdrawTicket

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Allows a user with Operator permission to resubmit a failed withdrawal ticket to the approval queue. A withdrawal ticket may fail for several generic reasons &mdash; often it is a typo on the withdrawal request. A user with Operator permission can update a ticket and correct that kind of problem.

### Request

```json
{
    "OMSId": 0,
    "TicketId": 0
}
```

| Key      | Value                                                        |
| -------- | ------------------------------------------------------------ |
| OMSId    | **integer.** The ID of the Order Management System through which the deposit is being made. |
| TicketId | **integer.** The ID of the withdrawal ticket, as assigned by the system. You can obtain a value for *TicketId* from both the **GetWithdrawTickets** and **GetAllWithdrawTickets** calls, where it is named *TicketNumber.* |

### Response

```json
{
    "result": true,
    "errormsg": "Invalid Request",
    "errorcode": 100,
    "detail": "Invalid OMSId"
}
```
The Response is a standard response object.

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean.** If the call has been successfully received by the Order Management System, *result* is *true;* otherwise it is *false.* |
| errormsg  | **string.** A successful receipt of the call returns *null.* The *errormsg* key for an unsuccessful call returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer.** A successful receipt of the call returns 0. An unsuccessful receipt of the call returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send.           |



