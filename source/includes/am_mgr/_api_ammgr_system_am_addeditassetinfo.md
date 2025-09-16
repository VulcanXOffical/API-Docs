## AM_AddEditAssetInfo

**Category:** System<br />**Permissions:** SUPERUSER<br />**Call Type:** Synchronous

Adds a new asset to the Asset Manager, or edits it.

This is a function handled by the Order Management System programmatically in most instances.

### Request

```json
{
    "assetManagerId": 0,
    "assetInfo": {
        "assetManagerId": 0,
        "omsId": 0,
        "assetId": 0,
        "assetShortCode": null,
        "assetFullName": null,
        "assetDescription": "",
        "defaultDepositProviderId": 0,
        "defaultWithdrawProviderId": 0,
        "assetType": 0,
        "assetSubType": 0,
        "action": 0,
        "messageType": 6006,
        "messageSequenceNumber": 0
    },
    "omsId": 0
}
```

| Key                       | Value                                                        |
| ------------------------- | ------------------------------------------------------------ |
| assetManagerId            | **integer.** The ID of the Asset Manager associated to which you're adding the ass. |
| omsId                     | **integer.** The ID of the Order Management System associated with the Asset Manager. |
| assetInfo                 | **json object.** Object consisting of the following key-value pairs. |
| assetManagerId            | **integer.** The ID of the Asset Manager for the asset. This field should be the same as *assetManagerId* above. |
| omsId                     | **integer.** The ID of the Order Management System that hosts the Asset Manager. |
| assetId                   | **integer.** The ID of the product (asset) you're adding to the Asset Manager. |
| assetShortCode            | **string.** A short name for the asset. BTC instead of BitCoin, for example. |
| assetFullName             | **string.** The full name of the asset. BitCoin instead of BTC, for example. |
| assetDescription          | **string.**  A brief description of the asset. "Cryptocurrency," for example. |
| defaultDepositProviderId  | **integer.** The ID of the Account Provider who handles deposits of this asset into the Exchange by default (other Account Providers may still handle the asset, although most usually there is only one). |
| defaultWithdrawProviderId | **integer.** The ID of the Account Provider who handles withdrawals of this asset from the Exchange by default (other Account Providers may still handle the asset, although most usually there is only one). |
| assetType                 | **integer.** The nature of the asset (product). One of:<br />**0** Unknown (an error condition)<br />**1** NationalCurrency<br />**2** CryptoCurrency<br />**3** Contract |
| assetSubType              | **long integer.**                                            |
| action                    | **integer.** An integer that describes which of its possible actions this call will do. One of:<br />**0** None<br />**1** Add<br />**2** Edit<br />**3** Delete |
| messageType               | **integer.** An integer that identifies this call as **AM_AddEditAssetInfo.** The value of *messageType* must match the call. The value of *messageType* for this call is 6006, because it deals with asset information. One of:<br />**6000** AssetManagerStreamCoreMessage<br />**6001** AssetManagerInfo<br />**6002** AddEditAccountInfo<br />**6003** AssetManagerStatistics<br />**6004** AccountAssetInfo<br />**6005** AccountProviderInfo<br />**6006** AssetInfo<br />**6007** TransactionSetRequest<br />**6008** AccountState<br />**6009** AccountAssetState<br />**6010** JsonState<br />**6011** ProcessedTransactionSet<br />**6012** ActionInfo_PendingDepositsUpdate<br />**6013** ActionInfo_PendingWithdrawUpdate<br />**6014** AddEditApiUser |
| messageSequenceNumber     | **integer.**                                                 |

### Response

```json
{
    "result": true,
    "errormsg": "",
    "statuscode": 0
}
```

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| result     | **Boolean.** If the call has been successfully received by the Order Management System, returns *true;* otherwise returns *false.* |
| errormsg   | **string.** A successful receipt of the call returns *null.* For an unsuccessful call, the value of *errormsg* can return:<br /><br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| statusCode | **integer.** If the value of *result* is *false,* *statusCode* can return:<br />**32** Not Authorized<br />**33** Asset_Manager_Not_Found |
