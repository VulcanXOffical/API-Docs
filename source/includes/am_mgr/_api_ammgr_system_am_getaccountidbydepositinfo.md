## AM_GetAccountIdByDepositInfo

**Category:** System<br />**Permissions:** SUPERUSER<br />**Call Type:** Synchronous

Returns the ID of the unknown account responsible for the supplied deposit information.

### Request

```json
{
    "OMSId": 0,
    "AssetManagerId": 0,
    "AccountProviderId": 0,
    "DepositInfo": null
}
```

| Key               | Value                                                        |
| ----------------- | ------------------------------------------------------------ |
| OMSId             | **integer.** The ID of the Order Management System associated with the Asset Manager. |
| AssetManagerId    | **integer.** The ID of the Asset Manager that has received deposits from an Account Provider and an unknown account. |
| AccountProviderId | **integer.** The ID of the Account Provider that handled the deposit into the Asset Manager for the unknown account. |
| DepositInfo       | **string.** The smoking gun.                                 |

### Response

```json
{
    "OMSId": 0,
    "AssetManagerId": 0,
    "AccountProviderId": 0,
    "AccountId": 0,
    "DepositInfo": null,
    "result": false,
    "errormsg": null,
    "statuscode": 0
}
```

| Key | Value |
| ---- | ---- |
| OMSId | **integer.** The ID of the Order Management System that is associated with the Asset Manager, Account Provider, and account, and through which a deposit was made. |
| AssetManagerId | **integer.** The ID of the Asset Manager that has received deposits from an Account Provider and an unknown account. |
| AccountProviderId | **integer.** The ID of the Account Provider that handled the deposit into the Asset Manager for the unknown account. |
| AccountId | **integer.** The ID of the account responsible for the deposit made through the Account Provider into the Asset Manager specified in the Request. |
| DepositInfo | **string.** |
| result     | **Boolean.** If the call has been successfully received by the Order Management System, returns *true;* otherwise returns *false.* |
| errormsg   | **string.** A successful receipt of the call returns *null.* For an unsuccessful call, the value of *errormsg* can return:<br /><br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| statusCode | **integer.** If the value of *result* is *false,* *statusCode* can return:<br />**32** Not Authorized<br />**33** Asset_Manager_Not_Found |


