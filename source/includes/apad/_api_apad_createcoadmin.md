## CreateCoAdmin

**Category:** APAD<br />**Permissions:** PlatformAdmin<br />**Call Type:** Asynchronous

Simultaneously creates a new user and designates that new user as company admin for the named company (issuer). The company must previously exist.

### Request

```json
{
    "sessionId":GUID,
    "companyName":"Windmill Farm, Inc.",
    "userName":"jsmith",
    "isEnabled":false,
    "email":"user@alphapoint.com",
    "password":"abracadabra"
}
```

| Key         | Value                                                        |
| ----------- | ------------------------------------------------------------ |
| sessionId   | **string.** The globally unique identifier for the current user's logged-in session. |
| companyName | **string.** The name of the company for which the new user will be company admin. |
| userName    | **string.** The login name of the new user on the system.    |
| isEnabled   | **Boolean.** A value of *true* signifies that the user's email account has been verified; a value of *false* signifies that the email account has not been verified. Defaults to *false*. If a user's email is *not* verified, the new user must go through a verification process on first log-in. If the email is verified, the user can log in without going through a verification process. |
| email       | **string.** The email address of the user being created and designated as company admin. |
| password    | **string.** The password of the user being created and designated as company admin. The password is sent in clear. |

### Reply

```json
{
    "Permissions":["CompanyAdmin"],
    "AssetNamesByCompanyName":["Windmill Farm, Inc.":"WMFS"],
    "OnExchangeBalancesByAssetName":["WMFS":100000],
    "OffExhangeBalancesByAssetName":[],
    "RoleNamesByCompanyName":["Windmill Farm, Inc.":"CoAdmin"],
    "UserName":"jsmith",
    "ExternalId":0000
}
```

| Key                             | Value                                                        |
| ------------------------------- | ------------------------------------------------------------ |
| Permissions                     | **string.** Returns an array of permissions that this user currently holds. The list is drawn from:<br />Enabled<br />PlatformAdmin<br />Investor<br />MarketMaker<br />CompanyAdmin<br />CompanyShareholder<br />CompanyAgent<br /><br />This is not an enumerated list. Because this is a new user being created as CompanyAdmin and that new user has not previously been on the system, the return should be *CompanyAdmin.* |
| AssetNamesByCompanyName         | **string.** DEPRECATED Returns a string array of key-value pairs that consist of the company name (*companyName* in the request) and the name of an asset provided by the company. A company may provide more than one asset. |
| OnExchangeBalancesByAssetName   | **array.** Returns an array of key-value pairs consisting of an asset name (one of the asset names returned in the *AssetNamesByCompanyName* field) and a number representing the amount of that asset belonging to the company and currently available on the exchange. |
| OffExachangeBalancesByAssetName | **array.** DEPRECATED Returns an array of key-value pairs consisting of an asset name (one of the asset names returned in the *AssetNamesByCompanyName* field) and a number representing the amount of that asset belonging to the company and *not* currently available on the exchange. In current implementations, usually returns and empty array. |
| RoleNamesByCompanyName          | **array.** Returns an array of key-value pairs consisting of the company name (*companyName* in the request) and the name of a role that this user has been given for this company. Since this is a new user without prior role, and the new user is being made a company admin, the role returned here should be *CoAdmin*. Roles may be:<br />CoAdmin<br />CoShareholder<br />CoAgent |
| UserName                        | **string.** The user name of the new user being created company administrator. |
| ExtnernalId                     | **string.** The user ID of the user being made a company admin, returned from the AlphaPoint Exhange as a string. |


