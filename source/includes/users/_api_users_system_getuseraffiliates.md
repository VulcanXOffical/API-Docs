## GetUserAffiliates

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Returns an array of users who are affiliates of the specified user.

An *affiliate user* is one whom the named user has encouraged to join the Exchange (using an *affiliate tag*). An Exchange may track these users and may offer some recompense to the base user. **GetUserAffiliates** produces a list of those users brought to the Exchange by the specified user.

### Request

```json
{
    "omsId": 0,
    "userId": 0
}
```

| Key    | Value                                                        |
| ------ | ------------------------------------------------------------ |
| omsId  | **integer.** The Order Management System on which the user is active. |
| userId | **integer.** The ID of the user whose affiliates you want to view. |

### Response

```json
[
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
]
```

The Response is an array of affiliated user records.

| Key                   | Value                                                        |
| --------------------- | ------------------------------------------------------------ |
| userId                | **integer.** The ID of *this* user, not the user with whom this user is affiliated. |
| userName              | **string.** The name of this user.                           |
| email                 | **string.** The email address of this user.                  |
| passwordHash          | **string.** Returns an empty string.       |
| pendingEmailCode      | **string.** Usually contains an empty string. During the time that a new user has been sent a registration email and before the user clicks the confirmation link, this value is a GUID. |
| emailVerified         | **Boolean.** The value is *true* if the email address in *email* has been verified by the registration process or directly by an Administrator; *false* if it has not. |
| accountId             | **integer.** The default account associated with this user.  |
| dateTimeCreated       | **string.** The date and time that this affiliation record was created, in Microsoft Ticks format and UTC time zone. |
| affiliateId           | **integer.** The ID of the user with whom this user is affiliated. |
| referrerId            | **integer.** The ID of the user who referred the affiliated user to the trading venue. The referrer user may or may not be the user to whom this user is affiliated. |
| omsId                 | **integer.** The ID of the Order Management System to which this user belongs. |
| use2FA                | **Boolean.** If *true* the affiliating user must use two-factor authentication during login; if *false* the affiliating user does not use 2FA. |
| salt                  | **string.** A unique value used for calculating the value of *passwordHash* from the password. The value of *passwordHash* is not revealed.  |
| pendingCodeTime       | **string.** The date and time that the user was offered a confirmation email, in Microsoft Ticks format and UTC time zone. |
| locked                | **Boolean.** *True* if this affiliated user is currently locked; *false* otherwise. A user may be locked by trying to log in too many times in rapid succession. He must be *unlocked* by an admin. |
| lockedTime            | **string.** The date and time that the affiliated user was locked, in Microsoft Ticks format and UTC time zone. |
| numberOfFailedAttempt | **integer.** If the affiliating user has attempted to log on and failed, this value is a count of those failed attempts. |


