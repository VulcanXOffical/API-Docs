## AM_GetAccountAssetDepositInfo

**Category:** System<br />**Permissions:** SUPERUSER<br />**Call Type:** Synchronous

Collects account deposit information based on Asset Manager ID, account ID, asset (product) ID, and Account Provider ID.

The call returns a single object with the collected information.

### Request

```json
{
    "assetManagerId": 0,
    "accountId": 0,
    "assetId": 0,
    "providerId": 0,
    "generateNewKey": true,
    "omsId": 0,
    "depositInfo": "",
    "ipAddress": ""
}
```

| Key            | Value                                                        |
| -------------- | ------------------------------------------------------------ |
| assetManagerId | **integer.** The ID of the Asset Manager from which the get the asset deposit information. |
| accountId      | **integer.** The ID of the single account for which you want to obtain asset deposit information. |
| assetId        | **integer.** The ID of the asset (product) whose deposits you want to return. |
| providerId     | **integer.** The ID of the Account Provider who handles deposits for this asset (product). Usually there is only one, but there can be more than one. |
| generateNewKey | **Boolean.**                                                 |
| omsId          | **integer.** The ID of the Order Management System on which the Asset Manager, account, and Account Provider function. |
| depositInfo    | **string.**                                                  |
| ipAddress      | **string.** The IP address of the Account Provider.          |

###  Result

```json
{
    "assetManagerId": 0,
    "accountId": 0,
    "assetId": 0,
    "providerId": 0,
    "depositInfo": "",
    "result": true,
    "errormsg": "",
    "statuscode": 0
}
```

| Key  | Value |
| ---- | ----- |
| assetManagerId | **integer.** The ID of the Asset Manager from which the get the asset deposit information. |
| accountId      | **integer.** The ID of the single account for which you want to obtain asset deposit information. |
| assetId        | **integer.** The ID of the asset (product) whose deposits you want to return. |
| providerId     | **integer.** The ID of the Account Provider who handles deposits for this asset (product). Usually there is only one, but there can be more than one. |
| depositInfo    | **string.**                                                  |
| result     | **Boolean.** If the call has been successfully received by the Order Management System, returns *true;* otherwise returns *false.* |
| errormsg   | **string.** A successful receipt of the call returns *null.* For an unsuccessful call, the value of *errormsg* can return:<br /><br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| statusCode | **integer.** If the value of *result* is *false,* *statusCode* can return:<br />**32** Not Authorized<br />**33** Asset_Manager_Not_Found |




