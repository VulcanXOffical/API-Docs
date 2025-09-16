## CreateUser

**Category:** APAD<br />**Permissions:** PlatformAdmin, CoAdmin<br />**Call Type:** Asynchronous

Creates a new user on the AlphaPoint Exchange along with a default account on the AlphaPoint Exchange for that user. The call also assigns the set of attributes listed in the Request.

### Request

```json
{
    "sessionId":GUID,
    "userName":"jsmith",
    "isEnabled":false,
    "isNotVerified":false,
    "isPlatformAdmin":false,
    "isInvestor":true,
    "isMarketMaker":true,
    "email":"user@alphapoint.com",
    "password":"abracadabra"
}
```

| Key             | Value                                                        |
| --------------- | ------------------------------------------------------------ |
| sessionId       | **string.** The globally unique identifier for the current user's logged-in session. |
| userName        | **string.** The log-in name of the user being created.       |
| isEnabled       | **Boolean.** A value of *true* signifies that the user's email account has been verified; a value of *false* signifies that the email account has not been verified. Defaults to *false*. If a user's email account has *not* been verified, the new user must go through a verification process on first log-in. If the email is verified, the user can log in without going through a verification process. |
| isNotVerified   | **Boolean.** DEPRECATED This value is *true* if the new user has *not* been verified automatically by a KYC (Know Your Customer) system, or manually by an AlphaPoint Exchange admin. The value is *false* if the new user has been verified. You can safely leave this field out of the Request. |
| isPlatformAdmin | **Boolean.** This value is *true* if the new user has been assigned the role of platform admin; the value is *false* if the new user has not been assigned this role. A CoAdmin calling **CreateUser** cannot create a PlatformAdmin, and this field defaults to *false*. |
| IsInvestor      | **Boolean.** This value is *true* if the new user is a qualified investor under the law.  |
| isMarketMaker   | **Boolean.** This value is *true* if the new user has the role of market maker. Only a market maker may quote on the AlphaPoint Exchange. |
| email           | **string.** The email address of the new user.               |
| password        | **string.** The password of the new user. This password is sent in clear. Note that the password is not confirmed in the response. |

### Reply

```json
{
    "Permissions":["Investor","MarketMaker"],
    "AssetNamesByCompanyName":["Windmill Farm, Inc.":"WMFS"],
    "OnExchangeBalancesByAssetName":["WMFS":100000],
    "OffExhangeBalancesByAssetName":[],
    "RoleNamesByCompanyName":["Windmill Farm, Inc.":"CoAdmin"],
    "UserName":"jsmith",
    "Email":"user@alphapoint.com",
    "ExternalId":0000
}
```


| Key                            | Value                                                        |
| ------------------------------ | ------------------------------------------------------------ |
| Permissions                    | **array.** Returns a string array of permissions that this user currently holds. The permissions are drawn from:<br />Enabled<br />PlatformAdmin<br />Investor<br />MarketMaker<br />CompanyAdmin<br />CompanyShareholder<br />CompanyAgent<br /><br />This is not an enumerated list. Because a new user is being created with the **CreateUser** call, permissions will not exist for the user except if any of the Booleans *isPlatformAdmin*, *isInvestor*, or *isMarketMaker* was set to *true* in the request. |
| AssetNamesByCompanyName        | **array.** DEPRECATED Returns a string array of key-value pairs that consist of a company name and the name of an asset provided by that company. Because the user has just been created and is not yet associated with any company, the *AssetNamesbyCompanyName* array will be empty. |
| OnExchangeBalancesByAssetName  | **array.** Returns an array of key-value pairs consisting of an asset name (usually one returned in the *AssetNamesByCompanyName* field) and a number representing the amount of that asset belonging to the company and currently available on the exchange. Because the user has just been created, and is not yet associated with a company, the *OnExchangeBalancesByAssetName* array will be empty. |
| OffExchangeBalancesByAssetName | **array.** DEPRECATED Returns an array of key-value pairs consisting of an asset name (one of the asset names returned by the *AssetNamesByCompanyName* field) and a number representing the amount of that asset belonging to the company and *not* currently available on the exchange. In current implementations, returns and empty array. |
| RoleNamesByCompanyName         | **array.** Returns an array of key-value pairs consisting of a company name and the name of a role that this user has been given for this company. Since this is a new user without a prior role or company connection (yet), this will return an empty array. |
| UserName                       | **string.** The name of the new user, echoed back from the Request. |
| Email                          | **string.** The email address of the new user, echoed back from the Request. |
| ExternalId                     | **string.** The AlphaPoint user ID of the user being created, returned as a string. |


