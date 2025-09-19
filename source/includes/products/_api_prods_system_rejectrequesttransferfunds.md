## RejectRequestTransferFunds

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Rejects a transfer of funds request.

Users with Trading permission can reject transfer requests only for transfers made from their own accounts; user with Operator permission can reject transfer requests made from any account.

### Request

```json
{
    "OMSId": 1,
    "OperatorId": 1,
    "RequestCode": ""
}
```

| Key         | Value                                                        |
| ----------- | ------------------------------------------------------------ |
| OMSId       | **integer.** The ID of the Order Management System on which the transfer request was made. |
| OperatorId  | **integer.** The ID of the user with Operator permission rejecting the transfer request. Users with Trading permission should just put 1 as the value of this key. |
| RequestCode | **string.** The globally unique ID (GUID) that identifies the specific transfer being rejected. |

### Response

```json
{
    "result": true,
    "requestcode": ""
}
```

| Key         | Value                                                        |
| ----------- | ------------------------------------------------------------ |
| result      | **Boolean.** If *true,* then the rejection request has been accepted by the system. If *false,* it has not. |
| requestCode | **string.** The globally unique ID (GUID) that identifies the specific transfer being rejected. |


