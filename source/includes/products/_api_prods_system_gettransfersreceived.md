## GetTransfersReceived

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Returns an array of received transfers for the specified account.

### Request

```json
{
    "OMSId": 1,
    "AccountId": 1
 }
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| OMSId     | **integer.** The ID of the Order Management System on which the transfers took place. |
| AccountId | **integer.** The ID of the account that initiated the transfers. |

### Response

```json
[
    {
        "transferId":0,
        "senderAccountId":0,
        "senderUserName":null,
        "receiverAccountId":0,
        "receiverUserName":null,
        "productId":0,
        "amount":0.0,
        "notes":null,
        "omsId":0
    },
]
```

| Key               | Value                                                        |
| ----------------- | ------------------------------------------------------------ |
| transferId        | **integer.** The ID of this transfer.                        |
| senderAccountId   | **integer.** The ID of the account that initiated (sent) the transfer. |
| senderUserName    | **string.** The user name of the user from *senderAccountId* who initiated the transfer. |
| receiverAccountId | **integer.** The ID of the account receiving the funds.      |
| receiverUserName  | **string.** The user name of the user from *receiverAccountId* who received the transfer. |
| productId         | **integer.** The ID of the product being transferred.        |
| amount            | **real.** The amount (or fractions) being transferred, in units of the product identified in *productId* (not dollar value). |
| notes             | **string.** Any notes appended to the transfer.              |
| omsId             | **integer.** The ID of the Order Management System on which the transfer took place. |




