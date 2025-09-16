## GetAccountFees

**Category:** System<br />**Permissions:** Operator, Trading, AccountReadOnly<br />**Call Type:** Synchronous

Retrieves a list of fee descriptions that apply to various instruments tradable by the account.

Users with Trading or AccountReadyOnly permissions can view fees for their own accounts; users with Operator permissions can view fees for any account.

### Request

```json
{
    "AccountId": 0,
    "OMSId": 0
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| AccountId | **integer.** The ID of the account for which fee information will be returned. |
| OMSId     | **integer.** The ID of the Order Management System on which the account resides. |

### Response

The Response is an array of fee objects. All fees apply to this account but the fees may refer to various instruments.

```json
[
    {
        "feeId": 0,
        "feeAmt": 0.0,
        "feeCalcType": 0,
        "feeType": 0,
        "ladderThreshold": 0.0,
        "ladderSeconds": 0,
        "isActive": false,
        "instrumentId": 0,
        "orderType": 0,
        "omsId": 0,
        "accountId": 0
    },
]
```

| Key             | Value                                                        |
| --------------- | ------------------------------------------------------------ |
| feeId           | **integer.** The ID of this fee structure.                   |
| feeAmt          | **real.** The fee assessed for trades in this instrument by this account. |
| feeCalcType     | **integer.** Determines the way that the fee is calculated. One of:<br />**0** FlatRate<br />**1** Percentage |
| ladderThreshold | **real.** If this account and instrument has a ladder fee structure, this is the threshold for this rung (increment) of the ladder, expressed in units of the instrument. |
| ladderSeconds   | **real.** DEPRECATED This key-value pair is no longer used.    |
| isActive        | **Boolean.** If *true,* this fee is active for this account and instrument. If *false,* the fee is not active. |
| instrumentId    | **integer.** The ID of the instrument subject to these fees for this account. |
| orderType       | **integer.** Describes the type of order this is. One of:<br />**0** Unknown (an error condition)<br />**1** Market order<br />**2** Limit<br />**3** StopMarket<br />**4** StopLimit<br />**5** TrailingStopMarket<br />**6** TrailingStopLimit<br />**7** BlockTrade |
| omsId           | **integer.** The ID of the Order Management System where this account resides subject to this fee structure. |
| accountId       | **integer.** The ID of the account subject to this fee structure for this instrument. |


