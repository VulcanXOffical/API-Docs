## CreateCompanyWithUser

**Category:** APAD<br />**Permissions:** PlatformAdmin<br />**Call Type:** Asynchronous

Simultaneously creates a new company and a new company administrator user login for that company. Neither the company nor company administrator user can previously exist.

<aside class="notice"><strong>Note: </strong>Essentially, <strong>CreateCompanyWithUser</strong> appends information about a new user to the <strong>CreateCompany</strong> call.</aside>

###Request

```json
{
    "sessionId":GUID,
    "companyName":"Windmill Farm, Inc.",
    "country":"USA",
    "stateOrProvinceOfIncorporation":"Delaware",
    "incorporationDate":"2018-08-17T17:57:56Z",
    "accountingCurrency":"USD",
    "userName":"jsmith",
    "isEnabled":false,
    "email":"user@alphapoint.com",
    "password":"abracadabra"
}
```

| Key                            | Value                                                        |
| ------------------------------ | ------------------------------------------------------------ |
| sessionId                      | **string.** The globally unique identifier for the current user's logged-in session. |
| companyName                    | **string.** The full name of the company being created.      |
| country                        | **string.** The name of the country where the new company has its headquarters. |
| stateOrProvinceOfIncorporation | **string.** The name of the state or province where the company is incorporated. (This may not be the location of the company's principal office.) |
| incorporationDate              | **string.** The time and date stamp of when the company was incorporated, in Microsoft Ticks format. The time and date are always given as UTC. |
| accountingCurrency             | **string.** The name of the currency in which the company does its accounting. For example, USD for US Dollars. |
| userName                       | **string.** The name of the administrative user being created along with the new company. |
| isEnabled                      | **Boolean.** A value of *true* signifies that the user's email account has been verified. Defaults to *false*. If a user's email is *not* verified, the new user must go through a verification process on first log-in. If the email address is verified, the user can log in without going through a verification process. |
| email                          | **string.** The email address of the new administrator user being created with the newly created company. |
| password                       | **string.** The password for the new administrative user. The password is sent in clear. |

### Reply

```
{
    "Company":"Windmill Farm, Inc.",
    "User":"jsmith"
}
```

The response confirms the company that you just created and the user who is the company administrator.

| Key     | Value                                                        |
| ------- | ------------------------------------------------------------ |
| Company | **string.** The name of the company that you just created.   |
| User    | **string.** The name of the user you just created as company administrator for the company. |


