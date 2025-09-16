## AddBalanceReconciliationInfo

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Adds balance and reconciliation information about an Account Provider to the Asset Manager of an AlphaPoint Exchange.

### Request

```json
{
    "infoId": 0,
    "currentColdBalance": 0.0,
    "currentHotBalance": 0.0,
    "totalExternalBalance": 0.0,
    "totalAMbalance": 0.0,
    "diffPercent": 0.0,
    "createdTime": "0001-01-01T00:00:00",
    "assetManagerId": 0,
    "accountProviderId": 0
}
```

| Key                  | Value                                                        |
| -------------------- | ------------------------------------------------------------ |
| infoId               | **integer.** The ID of this set of reconciliation information. |
| currentColdBalance   | **real.** The balance currently held in the Cold Wallet &mdash; a wallet not connected to the internet. |
| currentHotBalance    | **real.** The balance currently held in the Hot Wallet &mdash; a wallet that is connected to the internet and available for transfer. |
| totalExternalBalance | **real.** The total balance currently held in an account outside of (or "external to") the AlphaPoint Exchange. This may be the current Cold Wallet balance plus other external balances. |
| totalAMbalance       | **real.** The balance for the account currently shown in the AlphaPoint Asset Manager identified by the value of  *assetManagerId.* |
| diffPercent          | **real.**  Any difference between the Hot balance + the Cold balance and the total balance that the OMS shows as on the Exchange, expressed as a percentage:<br />(Hot + Cold)/totalAMBalance.                                                 |
| createdTime          | **string.** The time that the reconciliation is sent to the Account Provider, expressed in Microsoft Ticks format and UTC time zone. |
| assetManagerId       | **integer.** The ID of the AlphaPoint Asset Manager that holds the balances on the Exchange. |
| accountProviderId    | **integer.** ID of the Account Provider                      |

### Response

```json
{
    "result": true,
    "errormsg": "",
    "errorcode": 0,
    "detail": ""
}
```
| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean.** If the call has been successfully received by the Order Management System, *result* is *true;* otherwise it is *false.* |
| errormsg  | **string.** A successful receipt of the call returns *null.* The *errormsg* key for an unsuccessful call returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer.** A successful receipt of the call returns 0. An unsuccessful receipt of the call returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send.           |


