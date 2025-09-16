## CancelWithdraw

**Category:** System<br />**Permissions:** Withdraw<br />**Call Type:** Synchronous

Cancels a pending withdrawal.

Only users with Withdraw permission can cancel their own pending withdrawals. An admin (a user with Operator permission) may cancel a withdraw, but is more likely to reject a withdraw.

### Request

```json
{
    "OMSId": 1,
    "UserId": 1,
    "AccountId": 1,
    "RequestCode": "Request Code GUID"
}
```

| Key         | Value                                                        |
| ----------- | ------------------------------------------------------------ |
| OMSId       | **integer.** The ID of the Order Management System where the original withdraw ticket was created. |
| UserId      | **integer.** The user ID of the user canceling the withdrawal. |
| AccountId   | **integer.** The ID of the account from which the withdraw was made. |
| RequestCode | **string.** The globally unique ID (GUID) that identifies the specific withdraw that is being canceled.<br /><br />You can obtain the *RequestCode* for a specific withdrawal by calling **GetWithdraws** with the account ID and looking for the *withdrawCode* value that corresponds to this pending withdrawal. |

### Response

```json
{
    "result": true,
    "errormsg": "Operation Failed",
    "errorcode": 101,
    "detail": "Withdraw Ticket not found for OmsId, AccountId, RequestCode"
}
```

The response indicates that the system has received the **CancelWithdraw** Request, not that the withdraw ticket has been canceled. You can check the status of a withdraw ticket by using **GetWithdrawTicket.**

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean.** A successful receipt of the withdraw ticket cancellation request returns *true;* an unsuccessful receipt (an error condition) returns *false.* |
| errormsg  | **string.** A successful receipt of the withdraw ticket cancellation request returns *null;* the *errormsg* field for an unsuccessful request returns one of the following messages: <br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104) |
| errorcode | **integer.** A successful receipt of the withdraw ticket cancellation request returns 0. An unsuccessful receipt returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send. Usually *null.* |




