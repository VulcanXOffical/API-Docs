## SubmitBlockTrade

**Category:** User<br />
**Permissions:** Operator<br />
**Call Type:** Asynchronous

Reports an off-market trade has occurred between two parties.

Once reported, you can follow the trade using **GetAccountTrades** or **GetTradesHistory.**

###Request

> Example lockedIn:True request

```json
{
    "instrumentId":1,
    "accountId":5,
    "side":0,
    "counterPartyId": "3",
    "quantity":0.1,
    "limitPrice":5000.0,
    "omsId": 0,
    "lockedIn":true,
    "timestamp":158153615438   
}
```

> Example lockedIn:False set of requests

```json
{
    "instrumentId":1,
    "accountId":5,
    "side":0,
    "counterPartyId": "2",
    "quantity":0.1,
    "limitPrice":5000.0,
    "omsId": 0,
    "lockedIn":false,
    "timestamp":158153615438
}
{
    "instrumentId":1,
    "accountId":7,
    "side":1,
    "counterPartyId": "1",
    "quantity":0.1,
    "limitPrice":5000.0,
    "omsId": 0,
    "lockedIn":false,
    "timestamp":158153615438
}
```

| Key            | Value                                                        |
| -------------- | ------------------------------------------------------------ |
| instrumentId   | **integer.** The ID of the instrument being traded.          |
| accountId      | **integer.** The ID of the account making the report of the block trade. |
| side           | **integer.** A number that represents the side of the transaction associated with accountId. One of:<br />0 Buy<br />1 Sell<br />2 Short<br />3 Unknown (error condition) |
| counterPartyId | **string.** The badge of the other party in the off-market trade. |
| ClientOrderId  | **long integer.** If the Gateway Setting "OtcRequireCounterParty" is false, the caller can exclude *counterPartyId* and include *clientOrderId* to hit a working block trade order. |
| quantity       | **real.** The quantity on the instrument that was traded.    |
| limitPrice     | **real.** The price at which to execute the block trade.     |
| omsId          | **integer.** The ID of the Order Management System where the block trade is to be reported. |
| lockedIn       | **Boolean.** *True* if both parties to the block trade agree that one of the parties will report the trade for both sides(Only need to submit API call once). Otherwise, *false* and both sides need to submit API call. |
| timestamp      | **long integer.** The time that the block trade was submitted, in POSIX format.          |

### Response

```json
{
    "status":"Accepted",
    "errormsg":"",
    "OrderId": 22
}
```

| Key      | Value                                                        |
| -------- | ------------------------------------------------------------ |
| status   | **string.** If the order is accepted by the system, it returns "Accepted," if not, it returns "Rejected." One of:<br />Accepted<br />Rejected |
| errormsg | **string.** Any error message that the server returns.       |
| OrderId  | **long integer.** The ID assigned to the order by the server. This allows you to track the order later. |


