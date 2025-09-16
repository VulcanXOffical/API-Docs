## AddUserAccount

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Assigns an account to a user. Both user and account must previously exist.

To create an account, see **AddAccount.** To create a user, see **CreateUser.**

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
| accountId     | **integer.** The ID of the existing account that you want to assign to an existing user. |
| accountHandle | **string.** A human-readable, user-assigned name for the account. The *accountHandle* is checked for uniqueness at create-time by the Order Management System. |
| userId        | **integer.** The ID of the user to whom you are assigning the account. |
| userName      | **string.** The Exchange name of the user to whom you are assigning to the account. |

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
| detail    | **string.** Message text that the system may send.uj         |
