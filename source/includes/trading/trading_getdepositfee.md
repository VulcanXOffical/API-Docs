## GetDepositFee

**Category:** Trading<br />
**Permissions:** Operator, Trading, Deposit<br />
**Call Type:** Synchronous

Get a fee estimate for a deposit.

Deposit fee is something that can be set by an exchange operator in the AdminUI, it is set per product. One reason for an exchange to charge a deposit fee is to cover the gas fee during sweeping process just like for ERC-20 tokens.

In the newer versions of APEX(version 4.0 and above), deposit fees can have overrides based on Account Provider or Account ID, means that a deposit can be set to apply only for a specific Account Provider used during the deposit or the specific account doing the deposit.

A user with Trading or Deposit permissions can obtain deposit fee estimates only accounts with which the user is associated; a user with Operator permission can obtain deposit fee estimates for any account.

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("GetDepositFee", {
  OMSId: 1,
  AccountId: 1,
  ProductId: 1,
  Amount: 100,
  AccountProviderId: 5,
});
```

```http
POST /AP/GetDepositFee HTTP/1.1
Host: apialphapointuniversitystaging.cdnhop.net:8443
aptoken: 1287b2b0-76c8-4249-ad22-3204fe4f4028
Content-Type: application/json
Content-Length: 111

{
    "OMSId": 1,
    "AccountId": 1,
    "ProductId": 1,
    "Amount": 100,
    "AccountProviderId": 5
}
```

All fields in the table below are required in order to the the correct deposit fee estimate.

| Key       | Value                                                                                               |
| --------- | --------------------------------------------------------------------------------------------------- |
| OMSId     | **integer.** The ID of the Order Management System._required._                                      |
| AccountId | **integer.** The ID of the account making the deposit._required._                                   |
| ProductId | **integer.** The ID of the product intended to be deposited. Fees may vary with product._required._ |
| Amount    | **real.** The amount of product intended to be deposited._required._                                |

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

| Key          | Value                                                                |
| ------------ | -------------------------------------------------------------------- |
| FeeAmount    | **real.** The estimated amount of the fee for the indicated deposit. |
| TicketAmount | **real.** The amount of product intended to be deposited.            |
