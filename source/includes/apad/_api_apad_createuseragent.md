## CreateUserAgent

**Category:** APAD<br />**Permissions:** PlatformAdmin, CoAdmin<br />**Call Type:** Asynchronous

Creates a new user in the AlphaPoint exchange and assigns that user as an agent of the specified company. The company must already exist. 

A company agent (CoAgent, or CompanyAgent), can trade or act in other ways on the company's behalf &mdash; as opposed to simply holding some token or share in the company. A user may be named as CoAgent for more than one company.

A user with CoAdmin permission can create a company agent only for companies for which the CoAdmin user is administrator; a PlatformAdmin can create a company agent for any company.

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
| companyName | **string.** The company for whom the new user is named as agent. |
| userName    | **string.** The name of the new user who is agent.           |
| isEnabled   | **Boolean.** A value of *true* signifies that the user's email account has been verified; a value of *false* signifies that the email account has not been verified. Defaults to *false*. If a user's email account is *not* verified, the new user must go through a verification process on first log-in. If the email is verified, the user can log in without going through a verification process. |
| email       | **string.** The email of the new user being named as agent.  |
| password    | **string.** The password of the new user being named as agent. The password is sent in clear. Note that the password is not echoed by the Reply. |

### Reply

```json
{
    "Permissions":["CompanyAgent"],
    "AssetNamesByCompanyName":["windmill Farm, Inc.":"WMFS"],
    "OnExchangeBalancesByAssetName":["WMFS":100000],
    "OffExchangeBalancesByAssetName":[],
    "RoleNamesByCompanyName":["Windmill Farm, Inc.":"CoAgent"],
    "UserName":"jsmith",
    "Email":"user@alphapoint.com",
    "ExternalId":0000
}
```

| Key                            | Value                                                        |
| ------------------------------ | ------------------------------------------------------------ |
| Permissions                    | **array.** Returns a string array of permissions that this user currently holds. The permissions are drawn from:<br />Enabled<br />PlatformAdmin<br />Investor<br />MarketMaker<br />CompanyAdmin<br />CompanyShareholder<br />CompanyAgent<br /><br />This is not an enumerated list. Because the user is being created (and has no prior permissions or roles), the *Permissions* array should return only *CompanyAgent* &mdash; the permission that is being assigned by the call. |
| AssetNamesByCompanyName         | **array.** DEPRECATED Returns a string array of key-value pairs that consist of a company name and the name of an asset provided by the company. This user is being created but also being named as company agent, so *AssetNameByCompanyName* may return a list of assets provided to the exchange by the company. |
| OnExchangeBalancesByAssetName  | **array.** Returns an array of key-value pairs consisting of an asset name (usually one returned in the *AssetNameByCompanyName* field) and a number representing the amount of that asset belonging to the company and currently available on the exchange. |
| OffExchangeBalancesByAssetName | **array.** DEPRECATED Returns an array of key-value pairs consisting of an asset name (usually one returned in the *AssetNameByCompanyName* field) and a number representing the amount of the asset belonging to the company and *not* currently available on the exchange. In current implementations, usually returns an empty array. |
| RoleNamesByCompanyName         | **array.** Returns an array of key-value pairs consisting of a company name and the name of a role that this user has been given for this company. Since this is a new user who has been given only the company agent role (so far), this field should return the company name and *CoAgent*. |
| UserName                       | **string.** The name of the user being made an agent.        |
| Email                          | **string.** The email of the user being made an agent.       |
| ExternalId                     | **string.** The AlphaPoint user ID of the new user, returned as a string. |


