## CancelFailedWithdrawTicket

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Cancels any single failed or resubmitted-failed withdraw ticket.

Only a user with Operator permission can cancel a failed withdraw ticket.

### Request

```json
{
    "omsId": 0,
    "ticketId": 0
}
```

| Key      | Value                                                        |
| -------- | ------------------------------------------------------------ |
| omsId    | **integer.** The ID of the Order Management System on which the failed withdraw ticket was created. |
| ticketId | **long integer.** The ID of the specific ticket that must be canceled. |

### Response

```json
{
    "result": false,
    "errormsg": "Invalid Request",
    "errorcode": 100,
    "detail": "Invalid OMSId"
}
```

The response indicates that the system has received the **CancelFailedWithdrawTicket** Request, not that the failed withdraw ticket has been canceled. You can check the status of a withdraw ticket by using **GetWithdrawTicket.**

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean.** A successful receipt of the failed withdraw ticket cancellation request returns *true;* an unsuccessful receipt (an error condition) returns *false.* |
| errormsg  | **string.** A successful receipt of the failed withdraw ticket cancellation request returns *null;* the *errormsg* field for an unsuccessful request returns one of the following messages: <br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104) |
| errorcode | **integer.** A successful receipt of the failed withdraw ticket cancellation request returns 0. An unsuccessful receipt returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send. Usually *null.* |



