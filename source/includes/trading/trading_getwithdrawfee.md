## GetWithdrawFee

**Category:** Trading<br />
**Permissions:** Operator, Trading, Withdraw<br />
**Call Type:** Synchronous

Get a fee estimate for a withdrawal.

Withdraw fee is something that can be set by an exchange operator in the AdminUI, it is set per product. It can also be set programmatically using **SetOMSFee**.

A user with Trading or Withdraw permissions can obtain withdrawal fee estimates only accounts with which the user is associated; a user with Operator permission can obtain withdrawal fee estimates for any account.

### Request

```javascript
const { APEX } = require("VulcanX-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("GetWithdrawFee", {
  OMSId: 1,
  AccountId: 1,
  ProductId: 1,
  Amount: 100,
});
```

```http
POST /AP/GetWithdrawFee HTTP/1.1
Host: hostname goes here...
aptoken: 1287b2b0-76c8-4249-ad22-3204fe4f4028 //valid sessiontoken
Content-Type: application/json
Content-Length: 82

{
    "OMSId": 1,
    "AccountId": 1,
    "ProductId": 1,
    "Amount": 100
}
```

All fields in the table below are required in order to the the correct withdraw fee estimate.

| Key       | Value                                                                                               |
| --------- | --------------------------------------------------------------------------------------------------- |
| OMSId     | **integer.** The ID of the Order Management System trading the product._required._                  |
| AccountId | **integer.** The ID of the account making the withdrawal._required._                                |
| ProductId | **integer.** The ID of the product intended to be withdrawn. Fees may vary with product._required._ |
| Amount    | **real.** The amount of product intended to be withdrawn._required._                                |

### Response

```javascript
{
    "FeeAmount": 1.0000000000000000000000000000,
    "TicketAmount": 100
}
```

```http
{
    "FeeAmount": 1.0000000000000000000000000000,
    "TicketAmount": 100
}
```

| Key          | Value                                                                   |
| ------------ | ----------------------------------------------------------------------- |
| FeeAmount    | **real.** The estimated amount of the fee for the indicated withdrawal. |
| TicketAmount | **real.** The amount of product intended to be withdrawn.               |
