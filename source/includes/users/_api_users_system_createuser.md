## CreateUser

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Creates a new Exchange user.

### Request

```json
{
    "userInfo": {
        "userId": 0,
        "userName": "",
        "email": "",
        "passwordHash": "",
        "pendingEmailCode": "",
        "emailVerified": false,
        "accountId": 0,
        "dateTimeCreated": "0001-01-01T00:00:00",
        "affiliateId": 0,
        "refererId": 0,
        "omsId": 0,
        "use2FA": false,
        "salt": "",
        "pendingCodeTime": "0001-01-01T00:00:00",
        "locked": false,
        "lockedTime": "0001-01-01T00:00:00",
        "numberOfFailedAttempt": 0
    },
    "operatorId": 0,
    "affiliateTag": "",
    "userConfig": [
        {"Key”: “Config1”, “Value”: Config1Val”},
        {“Key”: “Config2”, “Value”: Config2Val”}
    ]
}
```
The Request contains a JSON *userInfo* object and an array of key-value pairs (if any) that apply to the user.

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| userInfo     | **string.** JSON *userInfo* object.                            |
| userId                | **integer.** The ID of this user.                            |
| userName              | **string.** The name of this user.                           |
| email                 | **string.** The email address of this user.                  |
| passwordHash          | **string.** Not currently used; returns empty string.        |
| pendingEmailCode      | **string.** Usually contains an empty string. During the time that a new user has been sent a registration email and before the user clicks the confirmation link, this value is a GUID. |
| emailVerified         | **Boolean.** The value is *true* if the email address in *email* has been verified by the registration process or directly by an Administrator; *false* if it has not. |
| accountId             | **integer.** The default account associated with this user.  |
| dateTimeCreated       | **string.** The date and time that this affiliation record was created, in Microsoft Ticks format and UTC time zone. |
| affiliateId           | **integer.** The ID of the user with whom this user is affiliated (if any). |
| referrerId            | **integer.** The ID of the user who referred this user to the trading venue (if any). The referrer user may or may not be the user to whom this user is affiliated. |
| omsId                 | **integer.** The ID of the Order Management System to which this user belongs. |
| use2FA                | **Boolean.** If *true* the user must use two-factor authentication during login; if *false* the user does not use 2FA. |
| salt                  | **string.** Reserved for future use; returns an empty string. |
| pendingCodeTime       | **string.** The date and time that the user was offered a confirmation email, in Microsoft Ticks format and UTC time zone. |
| locked                | **Boolean.** *True* if this user is currently locked; *false* otherwise. |
| lockedTime            | **string.** The date and time that the user was locked, in Microsoft Ticks format and UTC time zone. |
| numberOfFailedAttempt | **integer.** If the user has attempted to log on and failed, this value is a count of those failed attempts. |
| operatorId   | **integer.** The ID of the operator creating the user.       |
| affiliateTag | **string.** The alphanumeric tag used to identify new affiliating members. An affiliate tag allows a user to encourage others to join the Exchange and provides a way to track those new members back to the initiating user. |
| userConfig   | **string.** User Settings or Configuration Strings are key-value pairs associated with a user. When a user registers with the Exchange, he goes through a user verification process that collects identification information. The process may vary with the Exchange. Venue operators or regulators may require specific additional information for the user record. *userConfig* is an array of key-value pairs in a json string that provides a flexible method of adding those key-value pairs. Each element of the array consists of a *key* string and a *value* string (both are always strings). |

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
