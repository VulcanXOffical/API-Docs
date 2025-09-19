## Authenticate2FA

**Category:** Authentication<br />
**Permissions:** Public<br />
**Call Type:** Synchronous

### Request
```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("Authenticate2FA", {
  OMSId: 1
});
```

```http
POST /AP/Authenticate2FA HTTP/1.1
Host: hostname goes here...
Content-Type: application/json
pending2FaToken: db1f4eeb-1694-4147-bdfd-4cc915e1f5e4
Content-Length: 24

{
    "code": "235991"
}
```

Completes the second part of a two-factor authentication by sending the authentication token from the non-AlphaPoint authentication system to the Order Management System. The call returns a verification that the user logging in has been authenticated, and a token.

Here is how the two-factor authentication process works:

1. Call **webauthenticateuser**, or **authenticate** if using HTTP. The response will include a  *Pending2FAFAToken*. 
2. For HTTP, the *Pending2FAToken* will be used as a header in **authenticate2FA** call.
3. Call **authenticate2FA** with the token you received from the two-factor authentication program.

| Key    | Value                                                        |
| ------ | ------------------------------------------------------------ |
| Code   | **string**. *Code* holds the token obtained from the other authentication source. |


### Response
```json
{
    "Authenticated": true,
    "UserId": 2,
    "SessionToken": "db1f4eeb-1694-4147-bdfd-4cc915e1f5e4"
}
```


| Key           | Value                                                        |
| ------------- | ------------------------------------------------------------ |
| Authenticated | **Boolean**. A successful authentication returns *true*. Unsuccessful returns *false*. |
| SessionToken  | **string**. The *SessionToken* is valid during the current session for connections from the same IP address. If the connection is interrupted during the session, you can sign back in using the *SessionToken* instead of repeating the full two-factor authentication process. A session lasts one hour after the last-detected activity or until logout. |

>To send a session token to re-establish an interrupted session:

```json
{
  "SessionToken": "YourSessionToken"
}
```



