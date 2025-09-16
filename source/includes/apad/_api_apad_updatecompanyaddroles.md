## UpdateCompanyAddRoles

**Category:** APAD<br />**Permissions:** PlatformAdmin, CompanyAdmin<br />**Call Type:** Asynchronous

Adds the specified roles to the given user for the specified company. 

A user with CompanyAdmin permission can update company roles only for the admin's company; a PlatformAdmin can update roles for any user or company.

### Request

```json
{
    "sessionId":GUID,
    "companyName":"Windmill Farm, Inc.",
    "roleNames":["CompanyAdmin","CompanyShareholder"],
    "userName":"jdoaks"
}
```

| Key         | Value                                                        |
| ----------- | ------------------------------------------------------------ |
| sessionId   | **string.** The globally unique session identifier (GUID) for the logged-in user making the call. |
| companyName | **string.** The name of the company that is having its roles updated. |
| roleNames   | **array.** The specific roles being assigned to the user named in *userName.* |
| userName    | **string.** The user being assigned the roles listed in the *roleNames* array. |

### Reply

```json
{
    "CompanyId":0000,
    "CompanyName":"Windmill Farm, Inc.",
    "Roles":[
        {
            "RoleName":"CoAdmin",
            "UserNames":["jsmith","jdoe","bjones","jdoaks"],
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
| CompanyId                      | **integer.** The ID for the company associated with the user whose role is added. |
| CompanyName                    | **string.** The name of the company where the role is being added. |
| Roles                          | **array.** An array, each element of which lists a role within the company (CoAdmin, CoShareholder, CoAgent); an array of user names assigned to that role; and the name of the company in which that role was assigned. |
| UserNames                      | **array.** An array of strings listing the usernames of users associated in some way with the company named in the Request. |
| AssetNames                     | **array.** An array of strings listing the assets associated with the company named in the Request. |
| OnExchangeBalalncesByAssetName | **array.** An array of key-value pairs consisting of an asset name associated with the company named in the Request, and a number representing the amount of that asset belonging to the company and currently available on the exchange. |
| Country                        | **string.** The name of the country where the company is located. |
| StateOrProvinceOfIncorporation | **string.** The name of the state or province where the company is incorporated. This may not be the location of the principal office of the company. |
| IncorporationDate              | **string.** The date and time stamp of when the company was incorporated, in Microsoft Ticks format. The time and date are always given as UTC. |
| AccountingCurrency             | **string.** The name of the currency in which the company's accounting takes place. For example, USD for US Dollars. |
| OffExchangeBalancesByAssetName | **array.** DEPRECATED Returns an array of key-value pairs consisting of an asset name and a number representing the amount of that asset belonging to the company and not currently available on the exchange. In current implementations, returns an empty array. |


