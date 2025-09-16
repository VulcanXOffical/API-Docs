## GetUserAffiliateTag

**Category:** Trading<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

Returns an array of affiliate tags associated with the identified user. The exchange can use an affiliate tag to identify new users who join the exchange as a result of a recommendation from the identified user.

### Request

```javascript
const { APEX } = require("VulcanX-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise('GetUserAffiliateTag',{
    "OMSId": 1,
    "UserId": 6
})
```

```http
POST /AP/GetUserAffiliateTag HTTP/1.1
Host: hostname goes here...
Content-Type: application/json
aptoken: e6567bb5-0245-4cb3-b99e-b3adebe9c94c //valid session token
Content-Length: 38

{
    "OMSId": 1,
    "UserId": 6
}
```

| Key    | Value                                                        |
| ------ | ------------------------------------------------------------ |
| UserId | **integer.** The ID of the user whose affiliate tag you want to retrieve.If not set, affiliate tag of the currently logged-in user will be returned_optional._ |
| OMSId  | **integer.** The ID of the Order Management System on which the user operates._optional._ |

### Response

The response is a JSON object of affiliate tag information

```javascript
{
    "OMSId": 1,
    "UserId": 6,
    "AffiliateId": 7,
    "AffiliateTag": "sample"
}
```

```http
{
    "OMSId": 1,
    "UserId": 6,
    "AffiliateId": 7,
    "AffiliateTag": "sample"
}
```

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| OMSId        | **integer.** The ID of the Order Management System on which the user operates. This echoes the *omsId* in the request. |
| UserId       | **integer.** The ID of the user whose affiliate tag is returned. Echoes the *userId* in the request. |
| AffiliateId  | **integer.** Affiliate ID of the user, this is unique per user.                        |
| AffiliateTag | **string.** The tag that the user can share.                 |


