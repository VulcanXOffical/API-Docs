## GetAssets

**Category:** APAD<br />**Permissions:** PlatformAdmin, CompanyAdmin, CompanyAgent, CompanyShareholder<br />**Call Type:** Asynchronous

Returns an array of assets pertinent to the user's permission level, as determined by the session ID, which "knows" the logged-in user. Users with CompanyAdmin, CompanyAgent, or CompanyShareholder permission see only those assets appropriate to the company or companies with which they're associated; a PlatformAdmin can see all assets.

### Request

```json
{
    "sessionId":GUID
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| sessionId | **string.** The globally unique identifier (GUID) for the current user's logged-in session. The session ID allows the system to identify the user and the user's permissions. |

### Reply

```json
[
    {
        "AssetName":"WMFS",
        "AssetFullName":"Windmill Farm Shares",
        "CompanyName":"Windmill Farm, Inc.",
        "AssetId":GUID,
        "Decimals":2,
        "TotalIssued":1000000,
        "BoardApprovalDate":"2018-08-17T17:57:56Z",
        "Comments":""
    }
]
```

The reply returns an array of asset information, each element defining an asset visible to the user because of the user's company affiliation.

| Key               | Value                                                        |
| ----------------- | ------------------------------------------------------------ |
| AssetName         | **string.** The short or nickname of an asset visible to the logged-in user. For example "WMFS" for "Windmill Farm Shares." The call **CreateAsset** defines the asset name and the asset full name. |
| AssetFullName     | **string.** The long or full name of an asset visible to the logged in user. For example, "Windmill Farm Shares." The call **CreateAsset** defines the asset name and the asset full name. |
| CompanyName       | **string.** The name of the company that owns or provides the asset to the exchange. The calling user is associated with this company (or is a PlatformAdmin). |
| AssetId           | **string.** The globally unique identifier of the asset.     |
| Decimals          | **integer.** DEPRECATED The number of decimal places in which the asset is traded. For example, the US Dollar is traded to two decimal places. The maximum number of decimal places is eight. |
| TotalIssued       | **long integer.** The total number of asset units (shares or tokens) currently available on the AlphaPoint Exchange. (Not the total number of assets or shares issued or issuable globally.) |
| BoardApprovalDate | **string.** DEPRECATED The time- and date-stamp when the board of the company authorized the issuance of the asset (shares or tokens), in Microsoft Ticks format. The time and date are always given as UTC. |
| Comments          | **string.** DEPRECATED Any comment appended to the asset.    |


