## GetUserAffiliateCount

**Category:** Trading<br />
**Permissions:** Operator,Trading<br />
**Call Type:** Synchronous

Gets a count of users that were referred by a user.

### Request

```javascript
const { APEX } = require("VulcanX-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("GetUserAffiliateCount", {
  OMSId: 1,
  UserId: 5,
});
```

```http
POST /AP/GetUserAffiliateCount HTTP/1.1
Host: hostname goes here...
Content-Type: application/json
aptoken: e6567bb5-0245-4cb3-b99e-b3adebe9c94c //valid session token
Content-Length: 38

{
    "OMSId": 1,
    "UserId": 5
}
```

| Key    | Value                                                                             |
| ------ | --------------------------------------------------------------------------------- |
| OMSId  | **integer.** The ID of the OMS where the user belongs to._required._              |
| UserId | **integer.** The ID of the user for which to get number of affiliates._required._ |

### Response

```javascript
{
    "Count": 0
}
```

```http
{
    "Count": 0
}
```

Returns to total count or number of users referred by a specific user.
