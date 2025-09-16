## AM_GetAccountProviderInfoList

**Category:** System<br />**Permissions:** SUPERUSER<br />**Call Type:** Synchronous

Returns an *AccountProviderInfos* object that contains an array, each element of which is information about the Account Providers using the specified Asset Manager and Order Management System.

### Request

```json
{
    "assetManagerId": 0,
    "omsId": 0
}
```

| Key            | Value                                                        |
| -------------- | ------------------------------------------------------------ |
| assetManagerId | **integer.** The ID of the Asset Manager whose associated Account Providers you want to return. |
| omsId          | **integer.** The ID of the Order Management System associated with the Asset Manager specified by *assetManagerId.* |

### Response

```json
{
    "AccountProviderInfos": [
        {
            "assetManagerId": 0,
            "accountProviderTypeString": "",
            "assetId": 0,
            "accountProviderName": "",
            "isEnabled": false,
            "config": "",
            "isDefaultDepositProvider": true,
            "isDefaultWithdrawProvider": true,
            "action": 0,
            "providerMode": 0,
            "accountProviderId": 0,
            "omsId": 0,
            "messageType": 6005,
            "balanceConfigProfile": {
                "minimumHotWalletBalance": 0.0,
                "minimumHotWalletType": 0,
                "maximumHotWalletBalance": 0.0,
                "maximumHotWalletType": 0,
                "hotWalletReserveOverMinimum": 0.0,
                "reserveType": 0,
                "autoReduceHotBalance": true,
                "aggregateBalanceMismatchThreshold": 25.0,
                "mismatchThresholdType": 0,
                "isEnabled": true
            },
            "messageSequenceNumber": 0
        }
    ],
    "result": false,
    "errormsg": "",
    "statuscode": 0
}
```

| Key  | Value |
| ---- | ----- |
| result     | **Boolean.** If the call has been successfully received by the Order Management System, returns *true;* otherwise returns *false.* |
| errormsg   | **string.** A successful receipt of the call returns *null.* For an unsuccessful call, the value of *errormsg* can return:<br /><br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| statusCode | **integer.** If the value of *result* is *false,* *statusCode* can return:<br />**32** Not Authorized<br />**33** Asset_Manager_Not_Found |
| AccountProviderInfos | **array of json objects.** The value of *AccountProviderInfos* is an array of json objects, each element of which uses the following key-value pairs. |
| assetManagerId | **integer.** The ID of the Asset Manager associated with this Account Provider, the specified asset, and its balance. |
| accountProviderTypeString | **string.** unk |
| assetId | **integer.** The ID of the asset whose information is returned in this element of the *AccountProviderInfos* array. |
| accountProviderName | **string.** The name of the Account Provider associated with the asset and Asset Manager in this element of the *AccountProviderInfos* array. |
| isEnabled | **Boolean.** Is this Account Provider currently permitted to handle the asset specified by *assetId*? If the value is *true,* the AP is permitted to handle the asset; if *false,* the AP is not permitted to handle the asset. |
| config | **string.** probably an object |
| isDefaultDepositProvider | **Boolean.** Is this Account Provider the default Account Provider for deposits of the specified asset? (There can be only one default, but several APs can handle the same asset type). If *true,* the AP is the default deposit Account Provider for this asset. |
| isDefaultWithdrawProvider | **Boolean.** Is this Account Provider the default Account Provider for withdrawals of the specified asset? (There can be only one default, but several APs can handle the same asset type). If *true,* the AP is the default withdrawal Account Provider for this asset. |
| action | **integer.** enum |
| providerMode | **integer.** enum |
| accountProviderId | **integer.** The ID of the Account Provider. |
| omsId | **integer.** The ID of the Order Management System associated with both the Asset Manager and the Account Provider. |
| messageType | **integer.** enum |
| messageSequenceNumber | **integer.** |
| balanceConfigProfile | **json object.** The value of *balanceConfigProfile* is a json object (not an array) that consists of the following key-value pairs. |
| minimumHotWalletBalance | **real.** The minimum allowable hot wallet balance for the Account Provider on the Exchange. |
| minimumHotWalletType | **integer.** enum |
| maximumHotWalletBalance | **real.** The maximum allowable hot wallet balance for the Account Provider on the Exchange. |
| maximumHotWalletType | **integer.** enum |
| hotWalletReserveOverMinimum | **real.** The value of the reserve amount in the asset identified by *assetId* than an Account Provider must maintain above hot wallet minimum. |
| reserveType | **integer.** enum |
| autoReduceHotBalance | **Boolean.** |
| aggregateBalanceMismatchThreshold | **real.** A limit value for comparing an Account Provider's balance on the Exchange with its declared balance. |
| mistmatchThresholdType | **integer.** enum |
| isEnabled | **Boolean.** If *true,* the *balanceConfigProfile* is in force. If *false,* it is not. An Account Provider cannot operator on the Exchange without an enabled *balanceConfigProfile.* |


