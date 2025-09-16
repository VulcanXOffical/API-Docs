## AcceptWithdrawTicket

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Accepts a withdraw ticket for fiat currency. Withdrawals of cryptocurrency are automatically accepted (or rejected) by the system.

Only a user with Operator permission can accept a withdraw ticket.

A user can withdraw two types of product, cryptocurrency and fiat (national) currency. The sequences of status that each type of withdraw ticket goes through are slightly different.

### Request

```json
{
    "OMSId": 0,
    "TicketId": 0
}
```

| Key      | Value                                                        |
| -------- | ------------------------------------------------------------ |
| OMSId    | **integer.** The ID of the Order Management System on which the withdraw ticket was created. |
| TicketId | **long integer.** An ID supplied by the system when the ticket was created, and which identifies the ticket uniquely. |

### Response

```json
{
    "result": true,
    "errormsg": null,
    "errorcode": 0,
    "detail": null
}
```

The response indicates that the system has received the **AcceptWithdrawTicket** Request, not that the withdraw ticket has been accepted. You can check the status of a withdraw ticket by using **GetWithdrawTicket.**

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean.** A successful receipt of the withdraw ticket acceptance request returns *true;* an unsuccessful receipt (an error condition) returns *false.* |
| errormsg  | **string.** A successful receipt of the withdraw ticket acceptance request returns *null;* the *errormsg* field for an unsuccessful request returns one of the following messages: <br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104) |
| errorcode | **integer.** A successful receipt of the withdraw ticket acceptance request returns 0. An unsuccessful receipt returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send. Usually *null.* |


