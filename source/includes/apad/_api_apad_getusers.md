## GetUsers

**Category:** APAD<br />**Permissions:** PlatformAdmin, CoAdmin<br />**Call Type:** Asynchronous

Returns an array of user information for users over whom the calling user has control or users who hold a balance in an asset owned by the company of which the caller is an admin. PlatformAdmin users can see all users.

### Request

```json
{
    "sessionId":GUID
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| sessionId | **string.** The globally unique identifier (GUID) for the logged-in session of the calling user. This identifies the calling user, that user's associated companies, and that user's permissions. |

### Reply

```json
[
    {
        "Permissions":["CompanyAdmin","Investor"],
        "AssetNamesByCompanyName":["Windmill Farm, Inc":"WMFS"],
        "OnExchangeBalancesByAssetName":["WMFS":100000],
        "OffExchangeBalancesByAssetName":[],
        "RoleNamesByCompanyName":["Windmill Farm, Inc.":"CoAdmin"],
        "UserName":"jsmith",
        "Email":"user@alphapoint.com",
        "ExternalId":0000
    }
]
```

The response returns an array of user information. Users are returned if they are related to the calling user by having a role &mdash; shareholder, investor, marketmaker, etc. &mdash; in a company over which the caller has control or with which the calling user is associated. For example, user A is CoAdmin of Windmill Farm, Inc. User B is a shareholder in Windmill Farm, Inc., or is an agent of Windmill Farm, Inc. User B's information will be returned by this call from user A.

| Key                            | Value                                                        |
| ------------------------------ | ------------------------------------------------------------ |
| Permissions                    | **array.** Returns a string array of the returned user's permissions. This list is drawn from:<br />Enabled<br />PlatformAdmin<br />Investor<br />MarketMaker<br />CompanyAdmin<br />CompanyShareholder<br />CompanyAgent<br /><br />This is not an enumerated list. |
| AssetNamesByCompanyNames       | **array.** DEPRECATED Returns a string array of key-value pairs that consist of a company name and the name of an asset provided by that company. The user, the asset, or the company must be associated in some way with the calling user (or the calling user may be a PlatformAdmin). |
| OnExchangeBalancesByAssetName  | **array.** Returns an array of key-value pairs consisting of an asset name and a number representing the amount of that asset belonging to the company and currently available on the exchange. |
| OffExchangeBalancesByAssetName | **array.** DEPRECATED Returns an array of key-value pairs consisting of an asset name and a number representing the amount of that asset belonging to the company and *not* available on the exchange. In current implementations, returns an empty array. |
| RoleNamesByCompanyName         | **array.** Returns an array of key-value pairs consisting of a company name (associated with the calling user) and the name of a role that this user has been given for that company. Roles may be:<br />CoAdmin<br />CoShareholder<br />CoAgent<br /><br />This is not an enumerated list. |
| UserName                       | **string.** The user name of the user associated in some way with the calling user. |
| Email                          | **string.** The email of the user whose information is returned.                           |
| ExternalId                     | **integer.** The AlphaPoint exchange user ID of the user whose information is returned.    |


