## CreateAccountWithdrawInfo

**Category:** Trading<br />
**Permissions:** Operator,Withdraw<br />
**Call Type:** Synchronous

Creates a new withdraw info for an account to store and use later for withdrawals. The accountwithdrawinfo to that will be created is also known as the whitelisted withdraw address.

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("CreateAccountWithdrawInfo", {
  OMSId: 1,
  AccountId: 7,
  ProductId: 1,
  AccountIdentifier: "asfasfasdf11dasfasf11",
  Name: "Sample",
});
```

```http
POST /AP/CreateAccountWithdrawInfo HTTP/1.1
Host: hostname goes here...
Content-Type: application/json
aptoken: e6567bb5-0245-4cb3-b99e-b3adebe9c94c //valid session token
Content-Length: 136

{
    "OMSId": 1,
    "AccountId": 7,
    "ProductId": 1,
    "AccountIdentifier": "asfasfasdf11dasfasf11",
    "Name": "Sample"
}
```

| Key               | Value                                                                                          |
| ----------------- | ---------------------------------------------------------------------------------------------- |
| OMSId             | **integer.** The ID of the OMS where the account belongs to._required._                        |
| AccountId         | **integer.** The ID of the account for which the withdraw info will be created._required._     |
| ProductId         | **integer.** The ID of the product for which the withdraw info will be created for._required._ |
| AccountIdentifier | **string.** The actual withdraw address._required._                                            |
| Name              | **string.** Any string that can be used to identify the withdraw info._required._              |

### Response

```javascript
{
    "result": true,
    "errormsg": null,
    "errorcode": 0,
    "detail": "4ed30f50-b8ad-491b-823d-70acdfdeb0be" //ID of the account withdraw info
}
```

```http
{
    "result": true,
    "errormsg": null,
    "errorcode": 0,
    "detail": "4ed30f50-b8ad-491b-823d-70acdfdeb0be"
}
```
