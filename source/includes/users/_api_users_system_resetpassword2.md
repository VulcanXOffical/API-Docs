## ResetPassword2

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

**ResetPassword2** is called automatically (without programmer intervention) when a user clicks the email sent by **ResetPassword.** 

The process works like this:

1. **ResetPassword** sends a password reset email to the user identified by *UserName* in the Request of that call.
2. When the user clicks the link in the reset email, this action fills in the values for *UserId,* *Password,* and *PendingCode,* and communicates these values to **ResetPassword2.**
3. **ResetPassword2** is called automatically, and makes the changes to the Exchange, without further interaction with the user.

### Request

```json
{
    "UserId": "",
    "Password": "",
    "PendingCode": ""
}
```

| Key         | Value                                                        |
| ----------- | ------------------------------------------------------------ |
| UserId      | **string.** The ID of the user whose password is being changed. |
| Password    | **string.** The new password for the user.                   |
| PendingCode | **string.** A GUID (globally unique ID) that identifies the user. |

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


