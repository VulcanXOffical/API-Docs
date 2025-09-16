## RemoveUserAccount

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Breaks the association between a user and an account, but does not delete the user or the account from the Exchange.

You cannot delete either a user or an account from the Exchange.

### Request

```json
{
    "accountId": 0,
    "accountHandle": "",
    "userId": 0,
    "userName": ""
}
```

| Key           | Value                                                        |
| ------------- | ------------------------------------------------------------ |
| accountId     | **integer.** The ID of the account that you're separating from the user. |
| accountHandle | **string.** A user-defined account name that is checked by the Exchange at create-time. |
| userId        | **integer.** The ID of the user that you're separating from the account. |
| userName      | **string.** The name of the user.                            |

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




