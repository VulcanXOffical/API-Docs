## AddUserAffiliateTag

**Category:** Trading<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

Associates an affiliate tag to a user. An exchange operator boost signups by can encouraging its current users to invite others to join by rewarding a user for every invite. For a user to be rewarded for every successful invite he/she makes, he needs to send an invite link together with his **AffiliateTag**. A user with elevated permission can add an affiliate tag for another user. A user can only have 1 affiliate tag at a time, if there is already an existing affiliate tag for the user, the affiliate tag in the request will replace the existing one.

### Request

```javascript
const { APEX } = require("VulcanX-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise('AddUserAffiliateTag',{
    "OMSId": 1,
    "UserId": 6 //optional
    "AffiliateTag": "myaffiliatetag"
})
```

```http
POST /AP/AddUserAffiliateTag HTTP/1.1
Host: hostname goes here...
Content-Type: application/json
aptoken: e6567bb5-0245-4cb3-b99e-b3adebe9c94c //valid session token
Content-Length: 59

{
    "OMSId": 1,
    "UserId": 6, //Optional
    "AffiliateTag": "myaffiliatetag"
}
```

| Key          | Value                                                                                                                                                           |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| OMSId        | **integer.** The ID of the Order Management System on which the user operates._optional._                                                                       |
| UserId       | **integer.** ID of the user to whom the Affiliate tag will be added. If not specified, affiliate tag will be added for the user currently logged-in._optional._ |
| AffiliateTag | **string.** The alphanumeric tag that will be set for the user._required._                                                                                      |

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
| result    | **Boolean.** _True_ signifies that the server has received the request to associate the affiliate tag with a specific user (not that it has done so); _false_ signifies an error.                                                                                                                                           |
| errormsg  | **string.** A successful response returns _null_; the _errormsg_ parameter for an unsuccessful response returns one of the following messages: Not Authorized (_errorcode_ 20), Invalid Request (_errorcode_ 100), Operation Failed (_errorcode_ 101), Server Error (_errorcode_ 102), Resource Not Found (_errorcode_ 104) |
| errorcode | **integer.** A successful response returns 0. An unsuccessful response returns one of the _errorcodes_ shown in the _errormsg_ list.                                                                                                                                                                                        |
| detail    | **string.** Message text that the system may send. Usually _null_.                                                                                                                                                                                                                                                          |
