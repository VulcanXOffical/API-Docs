## CoinsOAuthAuthenticateUser	

**Category:** System<br />**Permissions:** Public<br />**Call Type:** Synchronous

Authenticates a user to the Exchange by accepting OAuth information.

The AlphaPoint Exchange communicates internally with the client system that uses OAuth. This allows the OAuth-using system to authenticate users, and the AlphaPoint Exchange accepts that user based on the values for *AccessCode* and *Email*. This avoids the necessity of a double login.

### Request

```json
{
    "AccessCode"= "",
    "Email"= ""
}
```
Note the equal signs rather than colons. The *OAuth* protocol requires equal signs.

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| AccessCode | **string.** An alphanumeric access code obtained from the OAuth authentication source. |
| Email      | **string.** The authenticating user's email address. The email address must already exist on the Exchange and must be unique on the Exchange. |

### Response

```json
{
    "CoinsOAuthAuthenticated": true,
    "User": "",
    "AccessToken": ""
}
```

| Key                     | Value                                                        |
| ----------------------- | ------------------------------------------------------------ |
| CoinsOAuthAuthenticated | **Boolean.** The value is *true* if the user has been authenticated by the ConsO protocol. The value is *false* otherwise. |
| User                    | **string.** The user name of the user being authenticated.   |
| AccessToken             | **string.** An alphanumeric session access token. If the connection is interrupted during the session, you can sign back in using the session token instead. A session token lasts one hour after the last-detected activity, or until logout. |


