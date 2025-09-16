## ConfirmRequestTransferFunds

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Confirms a transfer of funds request.

Users with Trading permission can confirm a funds transfer request only for their own funds transfers; users with Operator permission can confirm any funds transfer request.

### Request

```json
{
    "OMSId": 1,
    "RequestCode": "",
    "OperatorId": "1"
}
```

| Key         | Value                                                        |
| ----------- | ------------------------------------------------------------ |
| OMSId       | **integer.** The ID of the Order Management System on which the original transfer of funds request was made. |
| RequestCode | **string.** The globally unique ID (GUID) that identifies the specific transfer request that is being confirmed. |
| OperatorId  | **integer.** A user with Operator permission would put the Operator's ID here; a user with Trading permission would put the value 1 here. |

### Response

```json
{
    "result": true,
    "requestcode": ""
}
```

| Key         | Value                                                        |
| ----------- | ------------------------------------------------------------ |
| result      | **string.** A value of *true* signifies that the transfer of funds has been confirmed. A value of *false* signifies that &mdash; for whatever reason &mdash; the transfer has not been confirmed. |
| requestCode | **string.** The globally unique ID (GUID) that identifies the specific transfer request confirmation. If the transfer has not been confirmed, this value is empty. |


