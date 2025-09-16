## GetRecentAffiliateRegistrations

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Returns an array of user registration information for users who have joined the Exchange associated with a given affiliate tag and user.

An affiliate tag allows a user to encourage others to join the Exchange and provides a way to track new members back to the initiating user.

### Request 

```json
{
    "userId": 0,
    "tag": "",
    "startDate": "0001-01-01T00:00:00",
    "endDate": "0001-01-01T00:00:00"
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| userId    | **integer.** The ID of a user whose affiliating users you want to return. The initiating user of the array of affiliate registrations. |
| tag       | **string.** The affiliate tag for the initiating user.       |
| startDate | **string.** The date you want to begin returning records of affiliating users. In Microsoft Ticks format and UTC time zone. |
| endDate   | **string.** The date you want to stop returning records of affiliating users, in Microsoft Ticks format and UTC time zone. |

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
    },
]
```

The Response is an array of user records for users who have joined the Exchange using the affiliate tag of the user identified in the Request, and during the time period specified.

| Key                   | Value                                                        |
| --------------------- | ------------------------------------------------------------ |
| userId                | **integer.** The ID of this user.                            |
| userName              | **string.** The name of this user.                           |
| email                 | **string.** The email address of this user.                  |
| passwordHash          | **string.** Returns an empty string.        |
| pendingEmailCode      | **string.** Usually contains an empty string. During the time that a new user has been sent a registration email and before the user clicks the confirmation link, this value is a GUID. |
| emailVerified         | **Boolean.** The value is *true* if the email address in *email* has been verified by the registration process or directly by an Administrator; *false* if it has not. |
| accountId             | **integer.** The default account associated with this user.  |
| dateTimeCreated       | **string.** The date and time that this affiliation record was created, in Microsoft Ticks format and UTC time zone. |
| affiliateId           | **integer.** The ID of the user with whom this user is affiliated (if any). |
| referrerId            | **integer.** The ID of the user who referred this user to the trading venue (if any). The referrer user may or may not be the user to whom this user is affiliated. |
| omsId                 | **integer.** The ID of the Order Management System to which this user belongs. |
| use2FA                | **Boolean.** If *true* the user must use two-factor authentication during login; if *false* the user does not use 2FA. |
| salt                  | **string.** A unique value used for calculating the value for *passwordHash.* The value of *passwordHash* is not revealed. |
| pendingCodeTime       | **string.** The date and time that the user was offered a confirmation email, in Microsoft Ticks format and UTC time zone. |
| locked                | **Boolean.** *True* if this affiliated user is currently locked; *false* otherwise. A user may be locked by trying to log in too many times in rapid succession. He must be *unlocked* by an admin. |
| lockedTime            | **string.** The date and time that the user was locked, in Microsoft Ticks format and UTC time zone. |
| numberOfFailedAttempt | **integer.** If the user has attempted to log on and failed, this value is a count of those failed attempts. |


