## RemoveAccountConfig

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Removes a single key-value pair from the Account Configuration for a specified account.

### Request

```json
{
    "accountId": 0,
    "accountHandle": "",
    "key": ""
}
```

| Key           | Value                                                        |
| ------------- | ------------------------------------------------------------ |
| accountId     | **integer.** The ID of the account from whose configuration you want to remove the key-value pair. |
| accountHandle | **string.** A user-assigned name for the account.            |
| key           | **string.** The key portion of the key-value pair. This identifies the pair to remove. |

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
