## SetUserInfo

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Updates a subset of a user's information. To create a new user, use **CreateUser.** 

Once created, a user cannot be deleted, only edited. You can prevent a user from logging in by setting *emailVerified* to *false.* 

Users with Trading permission can set user info only for those users associated with the Trading user's default account; users with Operator permission can set user info for any user.

### Request

```json
{
    "userId": 0,
    "userName": "",
    "password": "",
    "email": "",
    "emailVerified": false,
    "accountId": 0,
    "use2FA": false
}
```
| Key           | Value                                                        |
| ------------- | ------------------------------------------------------------ |
| userId        | **integer.** The ID of the user whose information you're setting or editing. This value is assigned by the system and uniquely identifies the user. You cannot change this value. |
| userName      | **string.** The user name of the user whose information you're setting or editing. The value of *userName* is checked for uniqueness at the time the user was created. You cannot change the value of *userName.* |
| password      | **string.** The password of the user.                        |
| email         | **string.** The email address of the user. Each user must have a unique email address. |
| emailVerified | **Boolean.** The value is *true* if the email address in *email* has been verified by the registration process or directly by an Administrator; *false* if it has not. |
| accountId     | **integer.** The ID of the default account associated with the user. |
| use2FA        | **Boolean.** If *true,* the user must use two-factor authentication during login; if *false* the user does not use 2FA. |

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
| passwordHash          | **string.** Returns an empty string.        |
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




