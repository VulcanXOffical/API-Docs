## GetUserInfo

**Category:** System<br />**Permissions:** Operator, Trading, AccountReadOnly<br />**Call Type:** Synchronous

Returns user information about a specific user.

Users with Trading or AccountReadOnly permission can return user information only about users associated with the same account as they are; users with Operator permission can return user information about any user.

### Request

```json
{
    "OMSId": 0,
    "userId": 0
}
or
{
    "OMSId": 0,
    "userName": ""
 }
```
You can make the Request using either *userId* or *userName* to return information.

| Key      | Value                                                        |
| -------- | ------------------------------------------------------------ |
| OMSId    | **integer.** The ID of the Order Management System on which the user operates. |
| userId   | **integer.** The ID of the user whose information you want to return. |
| userName | **string.** The name of the user whose information you want to return. |

### Response

```json
{
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
}
```

| Key                   | Value                                                        |
| --------------------- | ------------------------------------------------------------ |
| userId                | **integer.** The ID of this user.                            |
| userName              | **string.** The name of this user.                           |
| email                 | **string.** The email address of this user.                  |
| passwordHash          | **string.** Returns an empty string.      |
| pendingEmailCode      | **string.** Usually contains an empty string. During the time that a new user has been sent a registration email and before the user clicks the confirmation link, this value is a GUID. |
| emailVerified         | **Boolean.** The value is *true* if the email address in *email* has been verified by the registration process or directly by an Administrator; *false* if it has not. |
| accountId             | **integer.** The default account associated with this user.  |
| dateTimeCreated       | **string.** The date and time that this affiliation record was created, in Microsoft Ticks format and UTC time zone. |
| affiliateId           | **integer.** The ID of the user with whom this user is affiliated (if any). |
| referrerId            | **integer.** The ID of the user who referred this user to the trading venue (if any). The referrer user may or may not be the user to whom this user is affiliated. |
| omsId                 | **integer.** The ID of the Order Management System to which this user belongs. |
| use2FA                | **Boolean.** If *true* the user must use two-factor authentication during login; if *false* the user does not use 2FA. |
| salt                  | **string.** A unique value used in calculating the value of *passwordHash.* The value of *passwordHash* is not revealed.  |
| pendingCodeTime       | **string.** The date and time that the user was offered a confirmation email, in Microsoft Ticks format and UTC time zone. |
| locked                | **Boolean.** *True* if this affiliated user is currently locked; *false* otherwise. A user may be locked by trying to log in too many times in rapid succession. He must be *unlocked* by an admin. |
| lockedTime            | **string.** The date and time that the user was locked, in Microsoft Ticks format and UTC time zone. |
| numberOfFailedAttempt | **integer.** If the user has attempted to log on and failed, this value is a count of those failed attempts. |


