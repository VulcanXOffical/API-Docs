## UpdateUserAffiliateTag

**Category:** Trading<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

Updates an existing affiliate tag of a user.

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise('UpdateUserAffiliateTag',{
    "AffiliateTag": "myaffiliatetag"
    "AffiliateId": 7
})
```

```http
POST /AP/UpdateUserAffiliateTag HTTP/1.1
Host: hostname goes here...
Content-Type: application/json
aptoken: e6567bb5-0245-4cb3-b99e-b3adebe9c94c //valid session token
Content-Length: 59

{
    "AffiliateTag": "myaffiliatetag",
    "AffiliateId": 7
}
```

| Key          | Value                                                                                                                         |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------- |
| OMSId        | **integer.** The ID of the Order Management System on which the user operates._optional._                                     |
| AffiliateId  | **integer.** The affiliate Id of the user, this id automatically gets assigned to a user upon registration/signup._required._ |
| AffiliateTag | **string.** The new affiliate tag to replace the existing one._required._                                                     |

###Response

```javascript
{
    "result": true,
    "errormsg": null,
    "errorcode": 0,
    "detail": null
}
```

```http
{
    "result": true,
    "errormsg": null,
    "errorcode": 0,
    "detail": null
}
```

| Key       | Value                                                                                                                                                                                                                                                                                                                       |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result    | **Boolean.** _True_ signifies that the server has received the request to update the affiliate tag with a specific user (not that it has done so); _false_ signifies an error.                                                                                                                                              |
| errormsg  | **string.** A successful response returns _null_; the _errormsg_ parameter for an unsuccessful response returns one of the following messages: Not Authorized (_errorcode_ 20), Invalid Request (_errorcode_ 100), Operation Failed (_errorcode_ 101), Server Error (_errorcode_ 102), Resource Not Found (_errorcode_ 104) |
| errorcode | **integer.** A successful response returns 0. An unsuccessful response returns one of the _errorcodes_ shown in the _errormsg_ list.                                                                                                                                                                                        |
| detail    | **string.** Message text that the system may send. Usually _null_.                                                                                                                                                                                                                                                          |
