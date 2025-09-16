## RegisterUser (API)

**Category:** System<br />**Permissions:** Public<br />**Call Type:** Synchronous

Registers a new user on the system. This is an API call; however, its contents are the same as **RegisterNewUser,** the REST version of the call.

A new user must go through a verification process, including email address verification, before being allowed to operate on the Exchange.

### Request

```json
{
    "UserInfo": {
        "UserName": "jsmith7",
        "passwordHash": "",
        "Email": "something@mailinator.com"
    },
    "UserConfig": [
        {"Key”": "Config1", "Value": "Config1Val"},
        {"Key": "Config2", "Value": "Config2Val"}
    ],
    "AffiliateTag": "",
    "OperatorId": 1
}"
```

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| UserInfo     | **json object.** The object contains information about the new user. |
| UserName     | **string.** The proposed Exchange user name for the new user. User names on the Exchange must be unique. |
| passwordHash | **string.** For the Request, the value of *passwordHash* is the assigned password for the new user (the user should change this at first opportunity).     |
| Email        | **string.** The new user's email address. The email address &mdash; as well as the new user &mdash; must go through a verification process before being allowed to operate on the Exchange. |
| UserConfig   | **array of json objects.** OPTIONAL CONTENT Configurations are key-value pairs of strings, usually named *key* and *value.* The value of *UserConfig* is an array of a variable number of json objects, each element of which is a key and a value. The information in the *UserConfig* varies from Exchange to Exchange depending on the needs of the venue and the regulatory environment in which it operates. |
| AffiliateTag | **string.** Leave this string empty. Affiliate tags can be added with **AddUserAffiliateTag.**  |
| OperatorId   | **integer.** Set this to 1 in a **Register~** Request. It is part of an object used elsewhere in the Exchange. |

### Response

```json
{
    "UserId": 1
}
```

| Key    | Value                                                        |
| ------ | ------------------------------------------------------------ |
| UserId | **integer.** The user ID of the new user on the Exchange. The user still must be verified on first log-in. |


