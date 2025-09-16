## CreateCompanyWithExistingUser

**Category:** APAD<br />**Permissions:** PlatformAdmin<br />**Call Type:** Asynchronous

Creates a new company and assigns an existing user as the company administrator (CoAdmin). There can be more than one company administrator assigned to a company. The user must already exist on the AlphaPoint Exchange, but can be any user. 

This call is similar to **CreateCoAdmin**, where a new user is created and assigned to an existing company; with **CreateCompanyWithExistingUser**, the user exists, but the company is created.

<aside class="notice"><strong>Note: </strong>Essentially, <strong>CreateCompanyWithExitingUser</strong> appends a user name to the <strong>CreateCompany</strong> call.</aside>

### Request

```json
{
    "sessionId":GUID,
    "companyName":"Windmill Farm, Inc.",
    "country":"USA",
    "stateOrProvinceOfIncorporation":"Delaware",
    "incorporationDate":"2018-08-17T17:57:56Z",
    "accountingCurrency":"USD",
    "userName":"jsmith"
}
```

| Key                            | Value                                                        |
| ------------------------------ | ------------------------------------------------------------ |
| sessionId                      | **string.** The globally unique identifier for the current user's logged-in session. |
| companyName                    | **string.** The name of the company being created.           |
| country                        | **string.** The name of the country where the company is located. |
| stateOrProvinceOfIncorporation | **string.** The name of the state or province where the company is incorporated. (This may not be the location of the company's principal office.) |
| incorporationDate              | **string.** The time and date stamp of when the company was incorporated, in Microsoft Ticks format. The time and date are always given as UTC. |
| accountingCurrency             | **string.** The name of the currency in which the company does its accounting. For example, USD for US Dollars. |
| userName                       | **string.** The user name of the user who will be new company's company admin (CoAdmin). The user must already exist on the AlphaPoint Exchange. |

### Reply

```json
{
    "Company":"Windmill Farm, Inc.",
    "User":"jsmith"
}
```

The response to the call confirms the user name and the company to which you are adding the user as company admin.

| Key     | Value                                                        |
| ------- | ------------------------------------------------------------ |
| Company | **string.** The name of the company to which the user is being added as company admin. |
| User    | **string.** The name of the user being added as company admin. |


