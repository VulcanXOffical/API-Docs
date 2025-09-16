## RemoveUserRole

**Category:** APAD<br />**Permissions:** PlatformAdmin, CompanyAdmin<br />**Call Type:** Asynchronous

Removes the specified role from the specified user.

A user with CompanyAdmin permission can remove a role only from a user belonging to a company for which the admin is CompanyAdmin; a PlatformAdmin can remove a role from any user.

### Request

```json
{
    "sessionId":GUID,
    "companyName":"Windmill Farm, Inc.",
    "roleName":"CoShareholder",
    "userName":"jdoaks"
}
```

| Key         | Value                                                        |
| ----------- | ------------------------------------------------------------ |
| sessionId   | **string.** The globally unique identifier (GUID) for the logged-in session by the calling user. |
| companyName | **string.** The name of the company associated with the user whose permission is to be removed. For CoAdmins calling **RemoveUserRole**, this also must be a company for which they are CoAdmin. |
| roleName    | **string.** The single role being removed from the user. The user retains any other existing roles. |
| userName    | **string.** The name of the user whose role is being removed. |

### Reply

```json
{
    "CompanyId":0000,
    "CompanyName":"Windmill Farm, Inc.",
    "Roles":[
        {
            "RoleName":"CoAdmin",
            "UserNames":["jsmith","jdoe","bjones"],
            "CompanyName":"Windmill Farm, Inc."
        },
        {
            "RoleName":"CoShareholder",
            "UserNames":["jsmith","tsmith","jdoaks"],
            "CompanyName":"Windmill Farm, Inc."
        },
        {
            "RoleName":"CoAgent",
            "UserNames":["jdoaks"],
            "CompanyName":"Windmill Farm, Inc."
        }
    ],
    "UserNames":[ "jsmith","jdoe","bjones","tsmith","jdoaks"],
    "AssetNames":["WMFS","JIV"],
     "OnExchangeBalancesByAssetName":[
        "WMFS":100000,"JIV":20000        
    ],
    "Country":"USA",
    "StateOrProvinceOfIncorporation":"Delaware",
    "IncorporationDate":"2018-08-17T17:57:56Z",
    "AccountingCurrency":"USD",
    "OffExchangeBalancesByAssetName":[]
}
```

The system replies with company information.

| Key                            | Value                                                        |
| ------------------------------ | ------------------------------------------------------------ |
| CompanyId                      | **integer.** The ID for the company associated with the user whose role is removed, as reported by the system when the company was created. |
| CompanyName                    | **string.** The name of the company as created.              |
| Roles                          | **array.** An array, each element of which lists a role within the company (CoAdmin, CoShareholder, CoAgent); an array of user names assigned to that role; and the name of the company in which that role was assigned. You should see that the role was successfully removed from the named user.  |
| UserNames                      | **array.** An array of strings listing the usernames of users associated in some way with the company named in the Request. |
| AssetNames                     | **array.** An array of strings listing the assets associated with the company named in the Request. |
| OnExchangeBalalncesByAssetName | **array.** An array of key-value pairs consisting of an asset name associated with the company named in the Request, and a number representing the amount of that asset belonging to the company and currently available on the exchange. |
| Country                        | **string.** The name of the country where the company is located. |
| StateOrProvinceOfIncorporation | **string.** The name of the state or province where the company is incorporated. This may not be the location of the principal office of the company. |
| IncorporationDate              | **string.** The date and time stamp of when the company was incorporated, in Microsoft Ticks format. The time and date are always given as UTC. |
| AccountingCurrency             | **string.** The name of the currency in which the company's accounting takes place. For example, USD for US Dollars. |
| OffExchangeBalancesByAssetName | **array.** DEPRECATED Returns an array of key-value pairs consisting of an asset name and a number representing the amount of that asset belonging to the company and not currently available on the exchange. In current implementations, returns an empty array. |


