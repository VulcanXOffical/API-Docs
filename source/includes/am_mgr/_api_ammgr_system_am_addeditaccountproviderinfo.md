## AM_AddEditAccountProviderInfo

**Category:** System<br />**Permissions:** SUPERUSER<br />**Call Type:** Synchronous

Adds or edits Account Provider information to the Asset Manager.

Before associating an Account Provider with an Asset Manager, both Account Provider and Asset Manager must already exist.

### Request

```json
{
    "assetManagerId": 0,
    "accountProviderTypeString": "",
    "assetId": 0,
    "accountProviderName": "",
    "isEnabled": false,
    "config": null,
    "isDefaultDepositProvider": false,
    "isDefaultWithdrawProvider": false,
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
        "autoReduceHotBalance": false,
        "aggregateBalanceMismatchThreshold": 25.0,
        "mismatchThresholdType": 0,
        "isEnabled": false
    	},
    "messageSequenceNumber": 0
}
```

| Key                               | Value                                                        |
| --------------------------------- | ------------------------------------------------------------ |
| assetManagerId                    | **integer.** The ID of the Asset Manager to which you're adding/editing an Account Provider. |
| accountProviderTypeString         | **string.**                                                  |
| assetId                           | **integer.** The ID of the product (asset) that the Account Provider handles. |
| accountProviderName                | **string.** The name of the Account Provider.                |
| isEnabled                         | **Boolean.** If *true,* the Account Provider is enabled in the Asset Manager. If *false,* then the Account Provider is not enabled. |
| config                            | **string.** The value of the *config* string varies with the Account Provider. See **Config Example** for one potential content example. |
| isDefaultDepositProvider          | **Boolean.** If *true,* this Account Provider is the default AP for deposits of the asset specified by *assetId.* If *false,* the AP can still handle the specified asset, but is not the default provider for deposits of that asset. |
| isDefaultWithdrawProvider         | **Boolean.** If *true,* this Account Provider is the default AP for withdrawals of the asset specified by *assetId.* If *false,* the AP can still handle the specified asset, but is not the default provider for withdrawals of that asset. |
| action                            | **integer.** An integer that describes which of its possible actions this call will do. One of:<br />**0** None<br />**1** Add<br />**2** Edit<br />**3** Delete |
| providerMode                      | **integer.** One of:<br />**0** Unknown (error condition)<br />**1** Aggregate<br />**2** Account |
| accountProviderId                 | **integer.** The ID of the Account Provider being associated with the Asset Manager. |
| omsId                             | **integer.** The ID of the Order Management System on which the Account Provide and Asset Manager operate. |
| messageType                       | **integer.** An integer that identifies this call to **AM_AddEditAccountProviderInfo.** The value of *messageType* must match the call. The value of *messageType* for this call is 6005, because it deals with Account Provider information. One of:<br />**6000** AssetManagerStreamCoreMessage<br />**6001** AssetManagerInfo<br />**6002** AddEditAccountInfo<br />**6003** AssetManagerStatistics<br />**6004** AccountAssetInfo<br />**6005** AccountProviderInfo<br />**6006** AssetInfo<br />**6007** TransactionSetRequest<br />**6008** AccountState<br />**6009** AccountAssetState<br />**6010** JsonState<br />**6011** ProcessedTransactionSet<br />**6012** ActionInfo_PendingDepositsUpdate<br />**6013** ActionInfo_PendingWithdrawUpdate<br />**6014** AddEditApiUser |
| messageSequenceNumber             | **integer.**                                                 |
| balanceConfigProfile              | **json object.** The *balanceConfigProfile* holds settings that an operator may want to set for an Account Provider. The value of *balanceConfigProfile* consists of the following fields. |
| minimumHotWalletBalance           | **real.** Sets the minimum allowable hot wallet balance for the Account Provider on the Exchange. The number here may be interpreted as either a percentage or an absolute value. |
| minimumHotWalletType              | **integer.** How the value for *minimumHotWalletBalance* is interpreted. One of:<br />**0** Percentage<br />**1** Absolute |
| maximumHotWalletBalance           | **real.** Sets the maximum allowable hot wallet balance for the Account Provider on the Exchange. The number here may be interpreted as either a percentage or an absolute value. |
| maximumHotWalletType              | **integer.** How the value for *maximumHotWalletBalance* is interpreted. One of:<br />**0** Percentage<br />**1** Absolute |
| hotWalletReserveOverMinimum       | **real.** Sets the value of the reserve amount in the assed identified by *assetId* that an Account Provider must maintain above hot wallet minimum. |
| reserveType                       | **integer.** The type of reserve that an operator imposes on an Account Provider. One of:<br />**0** Percentage (the reserve is a percentage of the hot wallet balance)<br />**1** Absolute (the reserve is an absolute quantity of the asset) |
| autoReduceHotBalance              | **Boolean.** If *true,* the Exchange automatically moves some of the asset specified by *assetId* from hot wallet to cold wallet. |
| aggregateBalanceMismatchThreshold | **real.** A limit value for comparing an Account Provider's hot and cold balances on the Exchange with its declared balance. This value may be interpreted as a percentage or as an absolute quantity. |
| mismatchThresholdType             | **integer.** How the value for *aggregateBalanceMismatchThreshold* is interpreted. One of:<br />**0** Percentage<br />**1** Absolute |
| isEnabled                         | **Boolean.** If *true,* the *balanceConfigProfile* is in force; if *false,* it is not. An Account Provider cannot operate on the Exchange without an enabled *balanceConfigProfile.* |

### Config Example

The contents of the *config* key-value pair vary from Account Provider to Account Provider. This is one example, but it is only an example.

> Config Example

```json
"Config": {
    "Asset": "MOBI",
    "IssuerAccount": "GA6HCMBLTZS5VYYBCATRBRZ3BZJMAFUDKYYF6AH6MVCMGWMRDNSWJPIH",
    "Trustline": "10000",
    "WalletUrl": "http://10.0.95.7:8000",
    "ColdWalletUrl": "https://horizon.stellar.org",
    "WalletId": " ",
    "ColdWalletId": " ",
    "WalletSecret": " ",
    "ColdWalletSecret": " ",
    "WalletNetworkPassphrase": "Public Global Stellar Network ; September 2015",
    "ColdWalletNetworkPassphrase": "Public Global Stellar Network ; September 2015",
    "Version": "234",
    "TestNetwork": "false"
    },
   "IsDefaultDepositProvider": true,
   "IsDefaultWithdrawProvider": true,
   "Action": "Edit",
   "ProviderMode": "0", // Aggregate = 1,Account = 2
   "AccountProviderId": 3,
   "OMSId": 1,
   "BalanceReconciliationInfo":[
      {
         "InfoId": 0,
         "CurrentColdBalance": 23,
         "CurrentHotBalance": 27.0196001,
         "TotalExternalBalance": 50.0196001,
         "TotalAMbalance": 0,
         "DiffPercent": 0,
         "CreatedTime": "2019-01-25T18:51:15Z",
         "AssetManagerId": 1,
         "AccountProviderId": 3
      }
   ],
   "AccountProviderDetails": {
      "HotWalletAccountBal": "27.0196001",
      "ColdWalletBal": "23.0000000",
      "lastKnownTimeStamp": "1/1/0001",
      "LastTransactionCursor": "95150310338629632"
      }
}

```


### Response
>Response

```json
{"AccountProviderInfo": {
    {
        "assetManagerId": 0,
        "accountProviderTypeString": "",
        "assetId": 0,
        "accountProviderName": null,
        "isEnabled": false,
        "config": null,
        "isDefaultDepositProvider": false,
        "isDefaultWithdrawProvider": false,
        "action": 0,
        "providerMode": 0,
        "accountProviderId": 0,
        "omsId":0,
    	"messageType": 6005,
        "balanceConfigProfile": {
            "minimumHotWalletBalance": 0.0,
            "minimumHotWalletType": 0,
            "maximumHotWalletBalance": 0.0,
            "maximumHotWalletType": 0,
            "hotWalletReserveOverMinimum": 0.0,
            "reserveType": 0,
            "autoReduceHotBalance": false,
            "aggregateBalanceMismatchThreshold": 25.0,
            "mismatchThresholdType": 0,
            "isEnabled": false
        	},
     	"messageSequenceNumber":0
		}
	},
"result": false,
"errormsg": "",
"statuscode": 0
}
```

| Key                               | Value                                                        |
| --------------------------------- | ------------------------------------------------------------ |
| result                            | **Boolean.** If the call has been successfully received by the Order Management System, *result* returns *true;* otherwise returns *false.* |
| errormsg                          | **string.** A successful receipt of the call returns *null.* For an unsuccessful call, the value of *errormsg* can return:<br /><br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| statusCode                        | **integer.** If the value of *result* is *false,* *statusCode* can return:<br />**32** Not Authorized<br />**33** Asset_Manager_Not_Found |
| AccountProviderInfo               | **json object.** The value of *AccountProviderInfo* consists of the following key-value pairs and objects. |
| messageSequenceNumber             | **integer.** A number that shows the order in which the call was received. |
| assetManagerId                    | **integer.** The ID of the Asset Manager with which you're associating the Account Provider. |
| AccountProviderTypeString         | **string.**                                                  |
| assetId                           | **integer.** The ID of the asset (product) that the Account Provider handles. |
| AccountProviderName               | **string.** The name of the Account Provider.                |
| isEnabled                         | **Boolean.** If *true,* the Account Provider is enabled in the Asset Manager. If *false,* then the Account Provider is not enabled. |
| config                            | **string.** The value of the *config* string varies with the Account Provider. See **Config Example** for one potential content example. |
| isDefaultDepositProvider          | **Boolean.** If *true,* this Account Provider is the default AP for deposits of the asset specified by *assetId.* If *false,* the AP can still handle the specified asset, but is not the default provider for deposits of that asset. |
| isDefaultWithdrawProvider         | **Boolean.** If *true,* this Account Provider is the default AP for withdrawals of the asset specified by *assetId.* If *false,* the AP can still handle the specified asset, but is not the default provider for withdrawals of that asset. |
| action                            | **integer.** An integer that describes which of its possible actions this call will do. One of:<br />**0** None<br />**1** Add<br />**2** Edit<br />**3** Delete |
| providerMode                      | **integer.** One of:<br />**0** Unknown (error condition)<br />**1** Aggregate<br />**2** Account |
| accountProviderId                 | **integer.** The ID of the Account Provider being associated with the Asset Manager. |
| omsId                             | **integer.** The ID of the Order Management System where the Asset Manager and the Account Provider operate. |
| messageType                       | **integer.** An integer that identifies this call to **AM_AddEditAccountProviderInfo.** The value of *messageType* must match the call. The value of *messageType* for this call is 6005, because it deals with Account Provider information. One of:<br />**6000** AssetManagerStreamCoreMessage<br />**6001** AssetManagerInfo<br />**6002** AddEditAccountInfo<br />**6003** AssetManagerStatistics<br />**6004** AccountAssetInfo<br />**6005** AccountProviderInfo<br />**6006** AssetInfo<br />**6007** TransactionSetRequest<br />**6008** AccountState<br />**6009** AccountAssetState<br />**6010** JsonState<br />**6011** ProcessedTransactionSet<br />**6012** ActionInfo_PendingDepositsUpdate<br />**6013** ActionInfo_PendingWithdrawUpdate<br />**6014** AddEditApiUser |
| balanceConfigProfile              | **json object.** The value of *balanceConfigProfile* consists of the following key-value pairs. |
| minimumHotWalletBalance           | **real.** Sets the minimum allowable hot wallet balance for the Account Provider on the Exchange. The number here may be interpreted as either a percentage or an absolute value. |
| minimumHotWalletType              | **integer.** How the value for *minimumHotWalletBalance* is interpreted. One of:<br />**0** Percentage<br />**1** Absolute |
| maximumHotWalletBalance           | **real.** Sets the maximum allowable hot wallet balance for the Account Provider on the Exchange. The number here may be interpreted as either a percentage or an absolute value. |
| maximumHotWalletType              | **integer.** How the value for *maximumHotWalletBalance* is interpreted. One of:<br />**0** Percentage<br />**1** Absolute |
| hotWalletReserveOverMinimum       | **real.** Sets the value of the reserve amount in the asset identified by *assetId* that an Account Provider must maintain above hot wallet minimum. |
| reserveType                       | **integer.** The type of reserve that an operator imposes on an Account Provider. One of:<br />**0** Percentage (the reserve is a percentage of the hot wallet balance)<br />**1** Absolute (the reserve is an absolute quantity of the asset) |
| autoReduceHotBalance              | **Boolean.** If *true,* the Exchange automatically moves some of the asset specified by *assetId* from hot wallet to cold wallet. |
| aggregateBalanceMismatchThreshold | **real.** A limit value for comparing an Account Provider's hot and cold balances on the Exchange with its declared balance. This value may be interpreted as a percentage or as an absolute quantity. |
| mismatchThresholdType             | **integer.** How the value for *aggregateBalanceMismatchThreshold* is interpreted. One of:<br />**0** Percentage<br />**1** Absolute |
| isEnabled                         | **Boolean.** If *true,* this balance configuration is enabled for the Account Provider on this Asset Manager. If *false,* the balance configuration is not enabled. |


