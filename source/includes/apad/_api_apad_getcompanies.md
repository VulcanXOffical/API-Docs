## GetCompanies

**Category:** APAD<br />**Permissions:** PlatformAdmin, CompanyAdmin, CompanyAgent, CompanyShareholder<br />**Call Type:** Asynchronous

Returns an array of companies pertinent to the permissions of the calling user, as determined by the session ID, which "knows" the logged-in user. Users with CompanyAdmin, CompanyAgent, or CompanyShareholder permission sees only those companies in which they have a role; a PlatformAdmin can see all companies.

### Request

```json
{
    "sessionId":GUID
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| sessionId | **string.** The globally unique identifier (GUID) for the current logged-in session. The session ID allows the system to identify the user and the user's permissions. |

### Reply

```json
[
    {
        "CompanyId":0000,
        "CompanyName":"Windmill Farm, Inc.",
        "Roles":[
            {
                "RoleName":"CoAdmin",
                "UserName":["jsmith","jdoe"],
                "CompanyName":"Windmill Farm, Inc."
            }
        ],
        "UserNames":["jsmith","jdoe","bjones"],
        "AssetNames":["WMFS"],
        "OnExchangeBalanceByAssetName":["WMFS":100000],
        "Country":"USA",
        "StateOrProvinceOfIncorporation":"Delaware",
        "IncorporationDate":"2018-08-17T17:57:56Z",
        "AccountingCurrency":"USD",
        "OffExchangeBalancesByAssetName":[]
    }
]
```

The reply returns an array of company information, each element defining a company in which the calling user has a role (a PlatformAdmin can see all companies).

| Key                             | Value                                                        |
| ------------------------------- | ------------------------------------------------------------ |
| CompanyId                       | **integer.** ID assigned by the system to the company.       |
| CompanyName                     | **string.** Name of the company with which the calling user is associated. |
| Roles                           | **array.** An array of a set of key-value pairs, each set consisting of:<br />*RoleName &mdash;* CoAdmin / CoShareholder / CoAgent<br />*UserName &mdash;* an array of users who hold that role in the company.<br />*CompanyName* &mdash; the name of the company in which the array of user names hold their roles. |
| UserNames                       | **array.** An array of strings listing the user names of users associated with this company. |
| AssetNames                      | **array.** An array of strings, each string listing the abbreviated name of an asset that this company brings to the exchange. |
| OnExchangeBalancesByAssetNames  | **array.** An array of key-value pairs consisting of an asset name and a number representing the amount of that asset belonging to the company and currently available on the exchange. |
| Country                         | **string.** The name of the country where the company is located. |
| StateOrProvinceOfIncorporation  | **string.** The name of the state or province where the company is incorporated. This may not be the principal office of the company. |
| IncorporationDate               | **string.** The date- and time-stamp of when the company was incorporated, in Microsoft Ticks format. Time and date are always given as UTC. |
| AccountingCurrency              | **string.** The currency in which the company's accounting takes place. For example, USD for US Dollars. |
| OffExchangeBalancesByAssetNames | **array.** DEPRECATED Returns an array of key-value pairs consisting of an asset name and a number representing the amount of that asset belonging to the company and *not* available on the exchange. In current implementations, usually an empty array. |


