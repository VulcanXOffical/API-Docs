## AM_AddEditAccountAssetInfo

**Category:** System<br />**Permissions:** SUPERUSER<br />**Call Type:** Synchronous

Adds or edits account asset information based on the Asset Manager ID.

### Request

```json
{
    "assetManagerId": 0,
    "accountAssetInfo": {
        "assetManagerId": 0,
        "accountId": 0,
        "assetId": 0,
        "action": 0,
        "messageType": 6004,
        "stateObjectId": "f393e52e-baba-44e1-91a4-e5efd94fdee4",
        "stateObjectIdString": "",
        "messageSequenceNumber": 0
    },
    "omsId": 0
}
```

| Key                   | Value                                                        |
| --------------------- | ------------------------------------------------------------ |
| assetManagerId        | **integer.** The ID of the Asset Manager associated with the account information. |
| omsId                 | **integer.** The ID of the Order Management System associated with the Asset Manager. |
| accountAssetInfo      | **json object.** Object consisting of the following fields.  |
| assetManagerId        | **integer.** The ID of the Asset Manager associated with the account. This field should be the same as *assetManagerId* above. |
| accountId             | **integer.** The ID of the account whose Asset Manager information you're adding or editing. |
| assetId               | **integer.** The ID of the Asset Manager product (asset) you're associating with the account. |
| action                | **integer.** An integer that describes which of its possible actions this call will do. One of:<br />**0** None<br />**1** Add<br />**2** Edit<br />**3** Delete |
| messageType           | **integer.** An integer that identifies this call to **AM_AddEditAccountAssetInfo.** The value of *messageType* must match the call. The value of *messageType* for this call is 6004, because it deals with account asset information. One of:<br />**6000** AssetManagerStreamCoreMessage<br />**6001** AssetManagerInfo<br />**6002** AddEditAccountInfo<br />**6003** AssetManagerStatistics<br />**6004** AccountAssetInfo<br />**6005** AccountProviderInfo<br />**6006** AssetInfo<br />**6007** TransactionSetRequest<br />**6008** AccountState<br />**6009** AccountAssetState<br />**6010** JsonState<br />**6011** ProcessedTransactionSet<br />**6012** ActionInfo_PendingDepositsUpdate<br />**6013** ActionInfo_PendingWithdrawUpdate<br />**6014** AddEditApiUser |
| stateObjectId         | **string.** GUID                                             |
| stateObjectIdString   | **string.** unk                                              |
| messageSequenceNumber | **integer.** unk                                             |

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


