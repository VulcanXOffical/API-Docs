## GetAccountConfig

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Returns an array of key-value configuration pairs for an account.

A user with Trading permission can get only the configuration pairs for the user's account; a user with Operator permission can get configuration pairs for any account.

You create a key-value configuration pair using **SetAccountConfig.**

### Request

```json
{
    "omsId": 0,
    "accountId": 0,
    "accountHandle": ""
}
```

| Key           | Value                                                        |
| ------------- | ------------------------------------------------------------ |
| omsId         | **integer.** The ID of the Order Management System that hosts the account. |
| accountId     | **integer.** The ID of the account whose key-value configuration pairs you want to get. |
| accountHandle | **string.** A user-assigned name for the account.            |

### Response

```json
[
    {
        "Key": "Config1",
        "Value": "Config1Val"
    }
]	
```

The Response returns an array of key names and their values.

| Key   | Value                                                        |
| ----- | ------------------------------------------------------------ |
| Key   | **string.** The name of the key being returned.              |
| Value | **string.** The value that corresponds to the *Key* string. Even numerical values are returned as strings. |


