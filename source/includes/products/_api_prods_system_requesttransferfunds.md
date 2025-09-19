## RequestTransferFunds

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Requests a transfer of funds.

### Request

```json
{
    "OMSId": 1,
    "ProductId": 1,
    "Amount": 1.00,
    "Notes": "",
    "ReceiverUserName": ""
}
```

| Key              | Value                                                        |
| ---------------- | ------------------------------------------------------------ |
| OMSId            | **integer.** The ID of the Order Management System on which the funds transfer request is made. |
| ProductId        | **integer.** The ID of the product in which the funds are denominated. The funds might be in US Dollars or BitCoin, for example. |
| Amount           | **real.** The units and fractions of product to be transferred, for example $2019.28 USD or 3.5 BitCoin (not the dollar value of the product). |
| Notes            | **string.** Any notes to be added to the transfer.           |
| ReceiverUserName | **string.** The Exchange username of the person receiving the transfer. |

### Response

```json
{
    "result": true,
    "requestcode": ""
}
```

| Key         | Value                                                        |
| ----------- | ------------------------------------------------------------ |
| result      | **Boolean.** If *true,* then the transfer request has been accepted by the system. If *false,* it has not. |
| requestCode | **string.** The globally unique ID (GUID) that identifies the specific transfer. |


