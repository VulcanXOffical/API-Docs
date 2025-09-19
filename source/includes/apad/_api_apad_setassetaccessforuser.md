## SetAssetAccessForUser

**Category:** APAD<br />**Permissions:** PlatformAdmin, CompanyAdmin<br />**Call Type:** Asynchronous

Specifies asset access for a user; that is, a user without asset access cannot obtain information about or trade in a specific asset.

A user with CompanyAdmin permission can set asset access only for a user belonging to a company for which the admin is CompanyAdmin; a PlatformAdmin can set asset access for any user.

### Request

```json
{
    "sessionId":GUID,
    "isEnabled":true,
    "userName":"jsmith",
    "assetName":"WMFS"
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| sessionId | **string.** The globally unique identifier (GUID) for the logged-in session by the calling user. |
| isEnabled | **Boolean.** A value of *true* allows the user to obtain information about and trade in this asset named in *assetName.* A value of *false* prevents the named user from obtaining information or trading in the asset. Thus, the Platform Admin or CompanyAdmin can turn access to the asset on or off for the user.|
| userName  | **string.** The user name of the user for whom asset access is being set. |
| assetName | **string.** The short name of the asset that is being made accessible to the user. For example, the asset Windmill Farm Shares might have the asset name WMFS. |

### Reply

```json
{
   "success":true
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| success   | **Boolean.** A value of *true* signifies that the system has received the request; a value of *false* that it has not. To check if the admin has changed the user's asset access, use the call **GetAssets.** |

