## SetUserVerificationLevel

**Category:** System<br />**Permission:** Operator<br />**Call Type:** Synchronous

Manually changes the value for a single user's verification level. Verification level is part of AlphaPoint's KYC ("Know Your Customer") process. The verification level for a user can be set either manually or via a third-party KYC service.

Only a user with Operator permission can change a user's verification level.

### Request

```json
{
    "UserId": 0,
    "VerificationLevel": 0
}
```

| Key               | Value                                                        |
| ----------------- | ------------------------------------------------------------ |
| UserId            | **integer.** The ID of the user whose verification level is being changed. |
| VerificationLevel | **integer.** The new value for the user's verification level (usually 0-9, but your system may have additional levels). |

### Response

```json
{
    "result": true,
    "errormsg": "",
    "errorcode": 0,
    "detail": ""
}
```
| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean.** If the call has been successfully received by the Order Management System, *result* is *true;* otherwise it is *false.* |
| errormsg  | **string.** A successful receipt of the call returns *null.* The *errormsg* key for an unsuccessful call returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer.** A successful receipt of the call returns 0. An unsuccessful receipt of the call returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send.           |

