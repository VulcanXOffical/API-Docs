## GetLoggedInUserBySessionToken

**Category:** System<br />**Permissions:** SUPERUSER<br />**Call Type:** Synchronous

Retrieves information about a logged-in user from the user's session token.

### Request

```json
{
    "SessionToken": "0f825e38-c0af-4089-ad7b-04f0e16a23f8"
}
```

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| SessionToken | **string.** The session token for this session, as provided by the system. |

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
| passwordHash          | **string.** Returns an empty string when it appears in a Response.        |
| pendingEmailCode      | **string.** Usually contains an empty string. During the time that a new user has been sent a registration email and before the user clicks the confirmation link, this value is a GUID. |
| emailVerified         | **Boolean.** The value is *true* if the email address in *email* has been verified by the registration process or directly by an Administrator; *false* if it has not. |
| accountId             | **integer.** The default account associated with this user.  |
| dateTimeCreated       | **string.** The date and time that this affiliation record was created, in Microsoft Ticks format and UTC time zone. |
| affiliateId           | **integer.** The ID of the user with whom this user is affiliated (if any). |
| referrerId            | **integer.** The ID of the user who referred this user to the trading venue (if any). The referrer user may or may not be the user to whom this user is affiliated. |
| omsId                 | **integer.** The ID of the Order Management System to which this user belongs. |
| use2FA                | **Boolean.** If *true* the user must use two-factor authentication during login; if *false* the user does not use 2FA. |
| salt                  | **string.** Contains a unique value used for calculating the value of *passwordHash* from the password. The value of *passwordHash* is not revealed.  |
| pendingCodeTime       | **string.** The date and time that the user was offered a confirmation email, in Microsoft Ticks format and UTC time zone. |
| locked                | **Boolean.** A user may be logged if the user tries to log in too many times in a short period. An admin must unlock the user. *True* if this user is currently locked; *false* otherwise. |
| lockedTime            | **string.** The date and time that the user was locked, in Microsoft Ticks format and UTC time zone. |
| numberOfFailedAttempt | **integer.** If the user has attempted to log on and failed, this value is a count of those failed attempts. |




