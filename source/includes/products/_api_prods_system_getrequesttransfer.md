## GetRequestTransfer

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Returns information about a single transfer of funds request that is still pending.

Users with Trading permission can get their own pending transfer of funds requests; users with Operator permission can get any pending transfer of funds request.

### Request

```json
{
    "omsId": 0,
    "operatorId": 0,
    "requestCode": null,
    "requestId": null,
    "payerUsername": null,
    "payerAccountId": null,
    "requestorUsername": null,
    "requestorAccountId": null,
    "productId": null,
    "amount": null,
    "amountOperator": null,
    "status": null,
    "startTimeStamp": null,
    "endTimeStamp": null
 }
```
The *requestor* (sic) is the person who requests the transfer and the *payer* is the person from whose holdings the amount is deducted.

| Key                | Value                                                        |
| ------------------ | ------------------------------------------------------------ |
| omsId              | **integer.** REQUIRED The ID of the Order Management System on which the pending funds transfer request was issued. |
| operatorId         | **integer.** REQUIRED For users with Operator permission, the ID of the operator-user; for users with Trading permission, put the value 1 in this field. |
| requestCode        | **string.** The globally unique ID (GUID) that identifies this specific funds transfer request. |
| requestId          | **string.** The ID of this funds transfer request, expressed as a string. |
| payerUsername      | **string.** The user name of the person from whose account holdings the amount is deducted.     |
| payerAccountId     | **string.** The account ID from which the amount is deducted.   |
| requestorUsername  | **string.** The user name of the person requesting the transfer.    |
| requestorAccountId | **string.** The account ID requesting the transfer.   |
| productId          | **string.** The ID of the product being transferred, expressed as a string. |
| amount             | **string.** The amount of the product being transferred (not its dollar value), expressed as a string. |
| amountOperator     | **string.**                                                  |
| status             | **string.**                                                  |
| startTimeStamp     | **string.** A date and time in Microsoft Ticks format and UTC time zone. |
| endTimeStamp       | **string.** A date and time in Microsoft Ticks format and UTC time zone. |

### Response

```json
{
    "omsId": 0,
    "operatorId": 0,
    "requestId": 0,
    "requestCode": "",
    "payerUsername": "",
    "payerAccountId": 0,
    "requestorUsername": "",
    "requestorAccountId": 0,
    "productId": 0,
    "productName": "",
    "amount": 0,
    "notes": "",
    "createdTimestamp": "0001-01-01T00:00:00",
    "lastUpdateTimestamp": "0001-01-01T00:00:00"
}
```

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| omsId               | **integer.** The ID of the Order Management System on which the pending funds transfer request was issued. |
| operatorId          | **integer.** The ID of the user with Operator permission who issued the call. For users with Trading permission, this shows 1. |
| requestId           | **integer.** The ID of the request that initiated the funds transfer. |
| requestCode         | **string.** The globally unique identifier (GUID) that identifies the request. |
| payerUsername       | **string.**                                                  |
| payerAccountId      | **integer.**                                                 |
| requestorUsername   | **string.**                                                  |
| requestorAccountId  | **integer.**                                                 |
| productId           | **integer.** The ID of the product being transferred.        |
| productName         | **string.** The name of the product being transferred.       |
| amount              | **integer.** The amount of the product being transferred (not the dollar value). This number is an integer only. |
| notes               | **string.** Any notes that have been entered about this transfer. |
| createdTimeStamp    | **string.** The time and date that the transfer was initiated, in Microsoft Ticks format and UTC time zone. |
| lastUpdateTimestamp | **string.** The time and date that the transfer status (or other information) was last updated, in Microsoft Ticks format and UTC time zone. |


