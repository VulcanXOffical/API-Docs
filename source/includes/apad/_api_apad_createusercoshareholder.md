## CreateUserCoShareholder

**Category:** APAD<br />**Permissions:** PlatformAdmin, CoAdmin<br />**Call Type:** Asynchronous

Creates a new user on the AlphaPoint Exchange and assigns that user the role of shareholder in a specific company. A company shareholder may possess shares or tokens in a company.

A user may be a shareholder in more than one company.

The company must already exist.

A user with CoAdmin permission can create a company shareholder only for companies for which the CoAdmin user is administrator; a PlatformAdmin can create a company shareholder for any company.

### Request

```json
{
    "sessionId":GUID,
    "companyName":"Windmill Farm, Inc.",
    "userName":"jsmith",
    "isEnabled":true,
    "email":"user@alphapoint.com",
    "password":"abracadabra"
}
```

| Key         | Value                                                        |
| ----------- | ------------------------------------------------------------ |
| sessionId   | **string.** The globally unique identifier for the current user's logged-in session. |
| companyName | **string.** The company in which the new user will be a shareholder. |
| userName    | **string.** The name of the new user who will be the shareholder. |
| isEnabled   | **Boolean.** A value of *true* signifies that the user's email account has been verified; a value of *false* signifies that the email account has not been verified. Defaults to *false*. If a user's email account is *not* verified, the new user must go through a verification process on first log-in. If the email is verified, the user can log in without going through a verification process. |
| email       | **string.** The email address of the user who is being created and made a shareholder. |
| password    | **string.** The password for the new user. Passwords are sent in clear. |

### Reply

```json
{
    "Permissions":["CompanyShareholder"],
    "AssetNamesByCompanyName":["Windmill Farm, Inc.":"WMFS"],
    "OnExchangeBalancesByAssetName":["WMFS":100000],
    "OffExchangeBalancesByAssetName":[],
    "RoleNamesByCompanyName":["Windmill Farm, Inc.":"CoShareholder"],
    "UserName":"jsmith",
    "Email":"user@alphapoint.com",
    "ExternalId":"0000"
}
```

| Key                            | Value                                                        |
| ------------------------------ | ------------------------------------------------------------ |
| Permissions                    | **array.** Returns a string array of permissions that this user currently holds. The permissions are drawn from:<br />Enabled<br />PlatformAdmin<br />Investor<br />MarketMaker<br />CompanyAdmin<br />CompanyShareholder<br />CompanyAgent<br /><br />This is not an enumerated list. Because the user is being created (and has no prior permissions or roles), the *Permissions* array should return only *CompanyShareholder* &mdash; the permission that is being assigned by the call. |
| AssetNamesByCompanyName        | **array.** DEPRECATED Returns a string array of key-value pairs that consist of a company name and the name of an asset provided by the company.  This user is being created, but also being named as a company shareholder of a specific company. *AssetNamesByCompanyName* should return a list of assets provided to the exchange by the company. |
| OnExchangeBalancesByAssetName  | **array.** Returns an array of key-value pairs consisting of an asset name (usually one returned in the *AssetNamesByCompanyName* field) and a number representing the amount of that asset belonging to the company and currently available on the exchange. |
| OffExchangeBalancesByAssetName | **array.** DEPRECATED Returns an array of key-value pairs consisting of an asset name (usually one returned in the *AssetNamesByCompanyName* field) and a number representing the amount of the asset belonging to the company and *not* currently available on the exchange. In current implementations, usually returns an empty array. |
| RoleNamesByCompanyName         | **array.** Returns an array of key-value pairs consisting of a company name and the name of a role that this user has been given for this company. Since this is a new user who has been given the company shareholder role by this call, this field should return the company name and *CoShareholder*. |
| UserName                       | **string.** The name of the new user being assigned the role of shareholder. |
| Email                          | **string.** The email address of the new user being assigned the role of shareholder. |
| ExternalId                     | **string.** The AlphaPoint user ID of the new user, returned as a string. |


