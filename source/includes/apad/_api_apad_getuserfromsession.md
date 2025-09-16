## GetUserFromSession

**Category:** APAD<br />**Permissions:** Any<br />**Call Type:** Asynchronous

Returns information about the specified user session, including username, email, and exchange balances. The caller must have correspond to the currently logged-in session ID. Thus, the **GetUserFromSession** call returns information about the calling user.

### Request

```json
{
    "sessionId":GUID
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| sessionId | **string.** The valid session ID the calling user. |


### Reply

```json
{
    "Permissions":["CompanyAdmin","Investor"],
    "AssetNamesByCompanyName":["Windmill Farm, Inc.":"WMFS","Jones Investments, LLC":"JIV"],
    "OnExchangeBalancesByAssetName":["WMFS":100000,"JIV":20000],
    "OffExchangeBalancesByAssetName":[],
    "RoleNamesByCompanyName":["Windmill Farm, Inc.":"CoAdmin","Jones Investments, LLC":"CoShareholder"],
    "UserName":"jsmith",
    "Email":"user@alphapoint.com",
    "ExternalId":0000
}
```

The system returns information about any user based on the session ID supplied in the Request.

| Key                            | Value                                                        |
| ------------------------------ | ------------------------------------------------------------ |
| Permissions                    | **array.** Returns a string array of the permissions that the user holds who is identified by the session ID in the Request. This list is drawn from:<br />Enabled<br />PlatformAdmin<br />Investor<br />MarketMaker<br />CompanyAdmin<br />CompanyShareholder<br />CompanyAgent<br /><br />This is not an enumerated list. |
| AssetNamesByCompanyName        | **array.** DEPRECATED Returns a string array of key-value pairs that consist of a company name and the name of an asset provided by that company. The companies are associated with the user named in the session ID of the Request. |
| OnExchangeBalancesByAssetName  | **array.** Returns an array of key-value pairs consisting of an asset name (string &mdash; one of the asset names returned in the *AssetNamesByCompanyName* field) and a number representing the amount of that asset belonging to the company and currently available on the exchange. These assets are those of companies that the user named in session ID is associated with. |
| OffExchangeBalancesByAssetName | **array.** DEPRECATED Returns an array of key-value pairs consisting of an asset name (one of the asset names returned in the *AssetNamesByCompanyName* field) and a number representing the amount of that asset belonging to the company and *not* currently on the exchange. In current implementations, usually returns an empty array. |
| RoleNamesByCompanyName         | **array.** Returns an array of key-value pairs consisting of a company name (a company associated with the user identified by the session ID in the Request) and the name of a role that this user has been given for that company. Roles may be:<br />CoAdmin<br />CoShareholder<br />CoAgent<br /><br />This is not an enumerated list. |
| UserName                       | **string.** The user name of the user identified by session ID in the Request. |
| Email                          | **string.** The email address of the user identified by the session ID in the Request. |
| ExternalId                     | **integer.** The user ID of the user identified by the session ID in the Request. |


